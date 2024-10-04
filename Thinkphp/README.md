# 9/28/24 进入ThinkPHP 的学习
  **注意！！ 为了便于理解thinkphp 和 thinkorm 的概念，可以使用对比理解，个人理解如下👇**<br>
**原生php写法——————>原生前端三件套**<br>
**thinkphp   ——————>vue框架**<br>
**thinkORM   ——————>vue components组件**

## 环境配置
> 在这之前：phpstudy; WAMP框架; php 8.0.2; composer 2.0+;
1. 安装thinkphp：在phpstudy软件WWW目录下，进入cmd，然后安装thinkphp :`composer create-project tp8`;
2. 测试一下，进入浏览器，输入：`127.0.0.1:8000`或者`localhost:8000`;如果要修改域名，在phpstudy中修改，路径为tp8 下的 public 文件夹；

## URL配置
位置：app/controller；
注意里面的文件名**首字母要大写**，文件内的类名需要与文件名**格式**和**名称**相同；
如果文件名为单个单词，则在浏览器中访问可以直接输入该名称的小写 👉 名称：`User`; url:`localhost:8000/index.php/user`;
如果文件名为多个单词，则在浏览器中访问则需要输入该名称的大/小写 👉 名称：`UserName`; url:`localhost:8000/index.php/UserName 或 localhost:8000/User_name`;

## 控制器
进入app文件夹，里面有配置好的“基础控制器”（Base controller），在该文件内写新的方法，所有继承这个类的控制器都能使用:
for example :
+ 直接在User.php 文件中调用 add 方法：
```php
//在 User.php 文件中
<?php
namespace app\controller;
use app\Base controller;

class User extends Base controller{
  public function add(){
    return 'add';
  }
}
```

+ 继承用法
```php
//在Base controller 中定义好方法 add ；
<?php
<!-- 前面部分与上段示例相同 -->
  public function add(){
    return parent::add();
}
```

### 多级控制器
1. 在 controller文件夹下再创建一个文件夹son1；
2. 在son1 中新建文件 son.php；
3. son.php 中写入代码：
```php
<?php
namespace app\controller\son1;
class Son 
    public function index()
    {
        return '123';
    }
}
```
4. 进入route/app.php， 新增代码：`Route::get('son1/son', 'son1.Son/index'); `
5. 结束，url输入:`http://tp8.com/index.php/son1/son` 页面会显示123，成功；

## 数据库
### 数据库的连接
修改.env文件和database.php文件的相关配置项即可（记得先用软件创建数据库）；
### 查询
`Db::name("form1") -> select();`
#### 单条数据的查询
使用 find方法：`Db::name("form1") -> where("id",1) ->find()` 这将查询form1表中的"id"字段为"1"的那一条数据；


# 10/4/24
### 新增
#### 新增单条数据
使用 insert(); 
1. 创建一个方法 ： `public function add(){}`
2. 创建一个新数组，存放新增数据： `$newarry = [(数组中的数据要与数据库中的字段名一一对应)];`
3. 执行 **insert** 方法：`$result = Db::name("dbname") -> insert($newarry);`
#### 新增多条数据
只需要将$newarry 变成一个二维数组即可;
#### 过滤新增数据
使用`strict()` 👉`Db :: name("dbname") -> strict(true) -> insert($newarry);`
#### 获取新增主键
使用`insertGetId()` 👉 `Db::name("user") -> insertGetId($newarry)`
#### replace 写入
`Db::name("dbname") -> replace() -> insert($newarry);` 以“修改”操作替代“插入”操作。
#### save() 新增
自行判断是插入操作还是修改操作；数据有主键就是修改，没有就是插入；`Db::name("dbname") -> save($newarry);`
