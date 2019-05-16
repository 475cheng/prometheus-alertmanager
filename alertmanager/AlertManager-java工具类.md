# AlertManager工具类的java调用实例 

## 1.引入alertmanager的jar包
``` pom.xml
<dependency>
    <groupId>com.bitauto.ep.fx</groupId>
    <artifactId>alertmanager</artifactId>
    <version>1.0.0.RELEASE</version>
</dependency>
```  

## 2.需要添加的配置如下：
``` application.properties
##alertmanager地址
alertmanager.postUrl=http://172.20.12.7:9093/api/v1/alerts
##项目名称
alertmanager.appId=chejia
##服务名称
alertmanager.service=java/c#等等
```  

## 3.调用实例：
``` java
		@Autowired
		private AlertClient alertClient;
		
        /*
          requestparam:请求接口的参数，实体转换成JSONString
          title：错误标题
          errormessage：错误描述
          e:代表捕获的异常类，用于打印错误栈信息
        */
		String s = alertClient.sendAlert("requestparam", "title", "errormessage", e);
```  

# 说明：
sendAlert方法内部会调用接口ClientMessageInter的默认实现类HttpClientMessage，如果想自定义实现类可以实现该接口，并加上@Primary@Component两个注解