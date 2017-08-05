##数据库操作

####通过JDBC访问数据库(mysql)

1. 加载数据库驱动  

```java
Class.forName("com.mysql.jdbc.Driver");
```

2.通过驱动管理类获取数据库链接

```java
connection = DriverManager.getConnection(URL,NAME,PASSWORD);
```
3.获取预处理statement，并设置参数
```java
 private  static String sqlSession ="select * from city where city_name= ?";
 preparedStatement = connection.prepareStatement(sqlSession);
 preparedStatement.setString(1,"常德市");
```
4. 向数据库发出sql执行查询，查询出结果集
```java
   resultSet = preparedStatement.executeQuery();
   while (resultSet.next()){
         System.out.println(resultSet.getString("id")+ " "+ resultSet.getString("description"));
   }
```
5.释放资源，关闭resultset，preparedstatement，connection
********
具体代码
```java
package com.Kmybatis.service;

import java.sql.*;

public class JdbcTest {

    private  static String URL = "jdbc:mysql://localhost:3306/springbootdb?characterEncoding=utf8&useSSL=false";
    private  static String NAME = "root";
    private  static String PASSWORD ="1001";
    private  static String sqlSession ="select * from city where city_name= ?";

    public static void main(String[] args) {


        Connection connection = null;
        PreparedStatement preparedStatement =null;
        ResultSet resultSet =null;
        try {
            Class.forName("com.mysql.jdbc.Driver");
            try {
                connection = DriverManager.getConnection(URL,NAME,PASSWORD);
                System.out.println(connection !=null);
                System.out.println("connected");
                preparedStatement = connection.prepareStatement(sqlSession);
                preparedStatement.setString(1,"常德市");
                resultSet = preparedStatement.executeQuery();
                while (resultSet.next()){
                    System.out.println(resultSet.getString("id")+ " "+ resultSet.getString("description"));
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }finally {
            if(resultSet != null){
                try {
                    System.out.println("resultSet is not null");
                    resultSet.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }if (preparedStatement !=null){
                try {
                    System.out.println("preparedStatement is not null");
                    preparedStatement.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }if(connection != null){
                try {
                    System.out.println("connection is not null");
                    connection.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }

        }

    }
}


```
