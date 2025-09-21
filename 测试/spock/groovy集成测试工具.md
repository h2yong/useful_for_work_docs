
```groovy
import groovy.json.JsonOutput
import groovy.json.StringEscapeUtils
// 将Unicode转为中文
def str= StringEscapeUtils.unescapeJava(JsonOutput.toJson(jsonParams))
// 将中文转为Unicode
StringEscapeUtils.escapeJava(str)
```

spock教程: https://spockframework.org/spock/docs/2.0/all_in_one.html