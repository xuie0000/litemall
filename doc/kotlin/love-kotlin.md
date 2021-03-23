## 使用Kotlin替换lombok

很烦`@Autowired`的警告提示，作者竟然一直没有替换，之前我喜欢用`@Resources`进行替换

前段时间我开始用`lombok`替换

昨天也尝试用了kotlin写了mybatis的示例，emmm..

```kotlin
@Service
class TestService(private val adminMapper: LitemallAdminMapper) {

    /**
     * 全量查询
     */
    fun list(): Any {
        val selectStatement = select(*LitemallAdminMapper.selectList)
                .from(LitemallAdminDynamicSqlSupport.litemallAdmin)
                .build()
                .render(RenderingStrategies.MYBATIS3)
//        return adminMapper.selectMany(selectStatement)
        return adminMapper.select(SelectDSLCompleter.allRows())
    }
}
```

可以和`lombok`说再见了

... litemall的吐嘈大会
