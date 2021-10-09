# Spring Boot 跨域处理

## @CrossOrigin 注解

直接在类或者方法上使用 ```@CrossOrigin``` 注解; 但这只能进行处理局部跨域。

## 注入 WebMvcConfigurer

注入 ```WebMvcConfigurer``` 处理全局跨域。

```java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOriginPatterns("*")
                .allowedMethods("*")
                .allowedHeaders("*")
                .allowCredentials(true)
                .maxAge(18000l);
    }
}
```

## 注入 CorsFilter

注入 ```CorsFilter``` 处理全局跨域。

```java
@Configuration
public class CorsConfig {
    @Bean
    public CorsFilter corsFilter() {
        final CorsConfiguration config = new CorsConfiguration();
        config.setAllowCredentials(true); // 允许发送 Cookie 和 HTTP 认证信息
        config.addAllowedOriginPattern("*"); // 当 AllowCredentials = true 且接受任意域名的请求(*) 的时候，必须使用 AllowedOriginPattern
        config.addAllowedHeader("*");// 允许访问的头信息,* 表示全部
        config.addAllowedMethod("*");// 允许提交请求的方法，* 表示全部允许
        config.setMaxAge(18000L);// 预检请求的有效期（秒），即在这个时间段里，对于相同的跨域请求不会再预检了

        final UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", config);

        return new CorsFilter(source);
    }
}
```
