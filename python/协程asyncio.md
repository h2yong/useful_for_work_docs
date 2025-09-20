# 协程asyncio

## Python3基于协程asyncio的消费者模式

原文链接：https://blog.csdn.net/haeasringnar/article/details/105870886

注意本例运行在Linux环境下  
本例模拟一个生产者每2-4秒生成一个消息，然后有多个消费者消费这些消息。  
暂定每个消费者消费一个消息耗时10秒，这样可以使每个消费者都能消费消息。

```python
import time
import asyncio
import queue
import threading
import uuid
import random
'''
基于协程的消费者模型，多个协程充当worker消费消息。
'''

now = lambda : time.time()

async def customer(num,q):
    print('任务 %d：start worker...' % num)
    while True:
        try:
            start = now()
            task = q.get(block=False)
            print('任务 %d：customer %s' % (num, task))
            await asyncio.sleep(10) # 假设每个消费者消费消息需要10秒，这样可以看出生产者生成的消息被不同的消费者消费
        except Exception as e:
            await asyncio.sleep(1)
            continue


async def run_async_customer(q):
    tasks = []
    for num in range(3):
        tasks.append(asyncio.create_task(customer(num,q)))
    await asyncio.gather(*tasks)

def product(q):
    print('product start...')
    while True:
        pro = '产品 %s' % str(uuid.uuid1())
        print(pro)
        q.put(pro)
        time.sleep(random.randint(2,4))

def run(q):
    asyncio.run(run_async_customer(q))


if __name__ == '__main__':
    q = queue.Queue()
    # 开启一个线程运行生产者
    prod = threading.Thread(target=product, args=(q,))
    # 开启一个线程运行所有的消费者
    cust = threading.Thread(target=run, args=(q,))
    prod.start()
    cust.start()
    prod.join()
    cust.join()
```

## asyncio.Queue生产者消费者实现示例
原文链接：https://juejin.cn/post/6844903902198906887

```python
import asyncio


async def consumer(n, q):
    print('consumer {}: starting'.format(n))
    while True:
        print('consumer {}: waiting for item'.format(n))
        item = await q.get()
        print('consumer {}: has item {}'.format(n, item))
        if item is None:
            # None 是一个停止信号。
            q.task_done()
            break
        else:
            await asyncio.sleep(0.01)
            q.task_done()
    print('consumer {}: ending'.format(n))


async def producer(q, num_workers):
    print('producer: starting')
    # 向队列中添加一些数字来模拟作业
    for i in range(num_workers * 30):
        await q.put(i)
        print('生产者: 添加任务 {} 到队列'.format(i))
        # 添加 None 到队列
    # 发出消费者退出的信号
    print('生产者: 向队列添加停止信号')
    for i in range(num_workers):
        await q.put(None)
    print('producer: waiting for queue to empty')
    await q.join()
    print('producer: ending')


async def main(loop, num_consumers):
    # 创建具有固定大小的队列，用于生产者
    # 将阻塞，直到消费者取出一些item。
    q = asyncio.Queue(maxsize=num_consumers)

    # 消费者任务调度
    consumers = [
        loop.create_task(consumer(i, q))
        for i in range(num_consumers)
    ]

    # 生产者任务调度
    prod = loop.create_task(producer(q, num_consumers))

    # 等待所有协程完成。
    await asyncio.wait(consumers + [prod])


event_loop = asyncio.get_event_loop()
try:
    event_loop.run_until_complete(main(event_loop, 2))
finally:
    event_loop.close()
```

## Python自带异步队列的大坑
原文链接：https://cloud.tencent.com/developer/article/1638916

```python
import asyncio
import random
import aiohttp


async def producer(queue):
    for _ in range(10):
        sleep_time = random.randint(1, 2)
        await queue.put(sleep_time)


async def consumer(queue):
    while True:
        sleep_time = await queue.get()
        size = queue.qsize()
        print(f"当前队列有：{size} 个元素")
        url = f"http://httpbin.org/delay/{sleep_time}"
        async with aiohttp.ClientSession() as client:
            resp = await client.get(url)
            print(await resp.text())


async def main():
    queue = asyncio.Queue(maxsize=3)
    asyncio.create_task(producer(queue))
    con = asyncio.create_task(consumer(queue))
    await con


asyncio.run(main())
```

其他参考文档：
- https://blog.csdn.net/weixin_39190382/article/details/130735835
- https://www.cnblogs.com/traditional/p/17398542.html
- https://www.seafog.cn/archives/481547087
- https://zhuanlan.zhihu.com/p/602955920