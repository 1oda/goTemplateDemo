# goTemplateDemo
##### 方案2：values变量写入

```yaml
values.yaml

common:
  use: rmq
# xsf rmq
rmq:
  hosts: ["192.168.1.1:10800","192.168.1.2:10800"]
  topic: mts_isol
```

将全链路的服务组件的配置维护values字段



```yaml
templates/calc.toml

[common]
use = {{ .Values.common.use }}
# xsf rmq
[rmq]
queue_size = 10000
consume_number = 40
hosts = {{ .Values.rmq.hosts }}
topic = {{ .Values.rmq.topic }}
# 消息队列服务连接超时时间
# millisecond
timeout = 500

[log]
level = error
path = "/log/server/calc.log"
format = "json"
console_print = false
```

go template方案 
