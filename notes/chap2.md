XML文档校验模式
    较为常见的验证模式有两种：DTD和XSD；

  DTD：
   DTD即文档类型定义，是一种XML约束模式语言，是XML文件的验证机制，属于XML文件组成的一部分。
   DTD是一种保证XML文档格式正确的有效方法，可以通过比较XML文档和DTD文件来看文档是否符合规范，元素和标签使用是否正确。
   一个DTD文档包含：元素的定义规则，元素的定义规则，元素间关系的定义规则，元素可使用的属性，可使用的实体或符号规则。

    要使用DTD验证模式的时候需要在XML文件的头部声明，以下是在Spring中使用DTD声明方式的代码：
    <?xml version="1.0" encoding="utf-8"?>
    <!DOCTYPE beans PUBLIC "-//Spring//DTD BEAN 2.0//EN" "http://www.Springframework.org/dtd
      Spring-beans-2.0.dtd">
    <beans>
    .....
    </beans>

  XSD
    XML Schema语言就是XSD（XML Schema Definition）, XML Schema描述了XML文档的结构，可以用一个指定的
    XML Schema来验证某个XML文档，以检查该XML文档是否符合其要求。文档设计者可以通过XML Schema指定XML文档所允许
    的结构和内容，并可以据此检查XML文档是否是有效的;XML Schame本身是XML文档，它符合XML语法结构，可以使用通用的XML解析器解析它。

    在使用XML Schema文档对XML实例文档进行检验，除了要声明名称空间（xmlns=http://www.Springframework.org/schema/beans）外,
    还必须指定该名称控件所对应的XML Schame文档的存储位置
    （xsi:schemaLocation="http://www.springframework.org/schema/beans
                        http://www.springframework.org/schema/beans/spring-beans.xsd"）



EntityResolver
    EntityResolver：如果SAX应用程序需要实现自定义处理外部实体，则必须实现EntityResolver接口，并使用setEntityResolver方法向
    SAX驱动器注册一个实例。
     也就是说 对于解析一个XML，SAX首先读取该XML文档上的声明，根据声明去寻找相应的DTD定义，以便对文档进行一个验证。默认的寻找规则是通过
     DTD的URI地址下载相应的DTD声明，并进行验证。下载的过程是一个漫长的过程，而且当网络中断或者不可用时，这里会报错，就是因为相应的DTD声明没有被找到的原因、

  EntityResolver的作用：
    项目本身就可以提供一个如何寻找DTD声明的方法，即由程序来实现寻找DTD声明的过程，比如我们将DTD文件放到项目中某处，在实现时直接将此文档
    读取并返回给SAX即可，这样就避免了通过网络来寻找相应的声明。




