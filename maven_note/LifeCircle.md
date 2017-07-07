
### Maven 生命周期

**目的**：对所有的构建过程进行抽象和统一

Maven的生命周期是抽象的，即生命周期本身不做任何实际的工作，
实际的任务都交由插件来完成(模板的设计模式)
> 构建过程包含项目的清理、初始化、编译、测试、打包、集成测试、验证、部署和站点生成

####三套生命周期
Maven用后三套相互独立的生命周期，分别为clean，default，site.
* **clean**：生命周期的目的是清理项目
* **default**：生命周期的目的是构建项目
* **site**：生命周期的目的是建立项目站点

每个生命周期包含一些阶段(phase)
 * **clean**: 包含pre-clean，clean，post-clean
 * **default**:包含validate，initialize，generate-source
                   process-source，generate-resource，
                   compile，process-classes-generate-test-sources
                   process-test-sources，generate-test-resources
                   test-compile，process-test-classes，test，
                   prepare-package，package，pre-integration-test，
                   integration-test，post-integration-test，verify，
                   install，deploy
                   
 * **site**：包含 pre-site，site，post-site，site-deploy
 
 ###### 内置绑定插件
 > 为了能让用户几乎不用任何配置就能够构建Maven项目，Maven在核心为一些
 生命周期阶段绑定了很多插件的目标
 
- eg: lifecircle ------>plugin:goal
- clean---->maven-clean-plugin:clean    
- site  --->maven-site-plugin:site
- site-deploy--->maven-site-plugin:deploy
- install ---->maven-intall-plugin:install
- package----->maven-jar-plugin:jar
- test-------->amven-surefire-plugin:test
and so on..

>默认打包类型jar之外，常见的打包类型还有war、pom、maven-plugin、ear

#### 获取插件信息
* 在线插件信息 Apache
             
