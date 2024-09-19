# WEBMAN   studying notes
> 环境要求：php ， composer2.0以上
## 创建项目
`composer create workerman/webman`

## 请求
通过 $request 可以获取请求相关的信息；
### 获得请求参数get
- 获取整个get数组 `$request -> get();`;
- 获取其中的某个值 `$request ->get('name');`; ~~如果不包含则返回null~~,也可以设置一个默认值，如果没找到对应值则返回默认值 `$request ->get('name','default_value');`;
> 获取post,header,cookie用法同上


#### 获得原始请求post包体
`$post = $request ->rawbody();`;

### 获取部分输入数据
从post，get的集合中获取部分值
only `$only = $request -> only(['account','pwd']);`  获取的数据
except `$only = $request -> except(['account','pwd']);`  除...外要获取的数据
