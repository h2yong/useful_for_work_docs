**典型的cypress测试代码如下：**

```javascript
describe('描述', () => {
    before(() => console.log('---- Test Start! ----'));
    beforeEach(() => cy.visit('https://witch.url'));
    afterEach(() => cy.clearCookies());

    it('测试用户交互', () => {
        cy.get('#app')
            .children('.intro')
            .click();
        cy.contains('Welcome').should('be.exist'); // BDD风格断言
    });

    it('测试显示文本', () => {
        cy.get('div').should('have.text', 'Hello');
        // * Chai风格断言
        cy.get('div').should(($div) => {
            const text = $div.text();
            expect(text).to.match(/hello/i);
        });
    });
});
```
**大致分为几个部分：**

* 运行器和生命周期（describe、it、before 等）
* 元素查找和操作（cy 相关命令）
* 断言/测试（should、expect、assert 多种风格）
