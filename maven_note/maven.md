### maven 依赖

#### 5 依赖范围

依赖范围就是用来控制依赖与编译classpath，测试classpath， 运行classpath的关系。
maven的集中依赖范围：

* **compile**： 编译依赖范围。如果没有指定，就会默认使用该依赖。作用范围 编译、测试、运行。
* **test**：    测试依赖范围，只对测试classpath有效
* **provided**： 已提供依赖范围。对编译和测试classpa有效，但在运行时无效。
* **runtime** ： 运行时依赖范围。
* **system** ： 系统依赖范围
----------------
 #### 6 传递性依赖&&依赖调解
 **作用**: 通过传递性依赖机制，将那些必要的间接依赖，以传递性依赖的形式引入到当前项目中。
 
  依赖调解：解决传递性依赖的多条依赖关系的问题
  
  
  #### 7 排除依赖
   
   作用：解除传递性依赖包含的项目。
   <exclusion>
      
   </exclusion>
    
  ### 8 归类依赖
  eg:
 <properties>
    <springframework.version>2.5.6</springframework.version>
 </properties>
 
 ---------------
 ### maven仓库
 
 分类：
   
  * 本地仓库
     
  * 远程仓库(中央仓库，私库，其他公共库)
     
   ```
       mvn clean install
   ```
