<template>
  <div class="reveal">
    <div class="slides">
      <section data-markdown>
        技术分享会

        1. Spring Cloud入门
        2. 对公司后台架构的探讨
        3. 辅助开发相关技术分享
        4. 将面向对象开发应用于复杂业务的一点心得
      </section>
      <section>
        <section data-markdown>
          1.Spring Cloud 入门
        </section>
        <section data-markdown>
          <script type="text/template">
            ###### 1. Spring Cloud之服务的注册与发现
            ![](https://img-blog.csdn.net/20171128095306816?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdsaDA0Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
          </script>
        </section>
        <section data-markdown>
          <script type="text/template">
            ###### 2. Spring Cloud之服务消费者和断路器
            Feign Client 和 Hystrix
            ![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1524217332235&di=30ecc68a29db3eddb98bc38b3992b961&imgtype=jpg&src=http%3A%2F%2Fimg1.imgtn.bdimg.com%2Fit%2Fu%3D66719541%2C299957653%26fm%3D214%26gp%3D0.jpg)
          </script>
        </section>
        <section data-markdown>
          <script type="text/template">
            ###### 3. Spring Cloud之配置中心
            ![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1524217536224&di=712bab284a0ade0b94d51c6b5a40204a&imgtype=jpg&src=http%3A%2F%2Fimg1.imgtn.bdimg.com%2Fit%2Fu%3D3122038461%2C220708831%26fm%3D214%26gp%3D0.jpg)
          </script>
        </section>
        <section data-markdown>
          <script type="text/template">
            ###### 4. Spring Cloud之路由网关
            ![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1524217623846&di=ac87d223738eba2375939dd051ee7523&imgtype=0&src=http%3A%2F%2Fimg.colabug.com%2F2017%2F07%2F8ec87dbfae23f1a8f9c4dfdf5bd023de.png)
          </script>
        </section>
      </section>
      <section>
         <section data-markdown>
           2.公司后台架构探讨
        </section>
        <section data-markdown>
          <script type="text/template">
          ![](../../../static/img/系统架构图.png)
          </script>
        </section>
      </section>
      <section>
        <section data-markdown>
          3.辅助开发相关技术分享

          1. lombok
          2. mapstruct
          3. flywaydb
          4. querydsl
          5. idea code generator
        </section>
        <section data-markdown>
          @NonNull: 可以帮助我们避免空指针。
          ```java
          import lombok.NonNull;
          public class NonNullExample extends Something {
            private String name;
            public NonNullExample(@NonNull Person person) {
              super("Hello");
              this.name = person.getName();
            }
          }
          ```
        </section>
        <section data-markdown>
          @Cleanup: 自动帮我们调用close()方法。
          ```java
          import lombok.Cleanup;
          import java.io.*;
          public class CleanupExample {
            public static void main(String[] args) throws IOException {
              @Cleanup InputStream in = new FileInputStream(args[0]);
              @Cleanup OutputStream out = new FileOutputStream(args[1]);
              byte[] b = new byte[10000];
              while (true) {
                int r = in.read(b);
                if (r == -1) break;
                out.write(b, 0, r);
              }
            }
          }
          ```
        </section>
        <section data-markdown>
          1. @Data: 自动为所有字段添加@ToString, @EqualsAndHashCode, @Getter方法
          2. @Slf4j: 自动生成日志对象
        </section>
        <section data-markdown>
          - MapStruct 可以将某几种类型的对象映射为另外一种类型，如将多个 DO（业务实体对象） 对象转换为 DTO（数据传输对象）
          - 使用方式也很简单，定义一个映射接口，声明映射方法，配上注解，MapSturct 就会实现此接口
        </section>
        <section data-markdown>
          Flyway 是独立于数据库的应用、管理并跟踪数据库变更的数据库版本管理工具。
        </section>
        <section data-markdown>
          QueryDSL简介
          1. QueryDSL仅仅是一个通用的查询框架，专注于通过Java API构建类型安全的SQL查询。
          2. Querydsl可以通过一组通用的查询API为用户构建出适合不同类型ORM框架或者是SQL的查询语句，也就是说QueryDSL是基于各种ORM框架以及SQL之上的一个通用的查询框架。
          3. 借助QueryDSL可以在任何支持的ORM框架或者SQL平台上以一种通用的API方式来构建查询。目前QueryDSL支持的平台包括JPA,JDO,SQL,Java Collections,RDF,Lucene,Hibernate Search
        </section>
        <section data-markdown>
          5. idea code generator
        </section>
      </section>
      <section data-markdown>
        面向对象开发应用于复杂业务一点心得
        ![](../../../static/img/积分消费管理V1.png)
      </section>

    </div>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    mounted(){
      Reveal.initialize({
        mouseWheel: true,
        progress: false,
        controls:false,
        dependencies: [
          { src: './static/reveal/plugin/markdown/marked.js' },
          { src: './static/reveal/plugin/markdown/markdown.js' },
          { src: './static/reveal/plugin/notes/notes.js', async: true },
          { src: './static/reveal/plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } }
        ]
      });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
  /*@import "HelloWorld.less";*/
</style>
