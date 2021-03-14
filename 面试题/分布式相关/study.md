# 一、网关

过滤器，责任链。反射。

比如：跨域Filter、请求鉴权Filter、反作弊Filter（egg：ip黑名单、uid黑名单、反爬虫等）、数据包完整性检查Filter（egg：定长Header+变长二进制Body）、协议转换Filter（egg：JSON->HashMap<String, Object>）、**路由转发（根据CMD转发到不同的业务逻辑层）**、服务治理（限流、降级、熔断等）

反作弊的ip等太多，可以用布隆过滤器。

路由：

通过URL找到目标method。进行反射调用。

- 自定义两个注解：RPCService（类）、RPCMethod（方法）
- Proxy启动扫描注解持久化到db，业务系统启动的时候Proxy也会扫描注解持久化到db
- 网关定时从db获取缓存到cache，截获请求查cache里class、method信息，反射调用目标方法
- 提供统一的对外接口给业务系统访问（egg：account-api）