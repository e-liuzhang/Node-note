# mongoose

+ 官网：https://mongoosejs.com/

## 1 MongoDB数据库的基本概念

+ 可以有多个数据库
+ 一个数据库中可以有多个集合（表）
+ 一个集合中可以有多个文档（表记录）
+ 文档结构灵活，没有任何限制
+ MongoDB非常灵活，不需要像MySQL一样先创建数据库、表、设计表结构
  + 只需要当插入数据时，指定往哪个数据库的哪个集合操作就行
  + 一切都由MongoDB帮你自动完成建库

```json
{
    qq:{
    	users:[
            {name:'张三',age:15},
            {name:'张三1',age:15},
            {name:'张三2',age:15},
            {name:'张三3',age:15},
            ...
        ],
        products:[
            
        ],
        ...
    },
    tapbao:{
        
    },
     baidu:{
         
     }
    
}
```



## 2 起步

安装：

```shell
npm i mongoose
```

hello world:

```javascript
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/test', {useNewUrlParser: true, useUnifiedTopology: true});

const Cat = mongoose.model('Cat', { name: String });

const kitty = new Cat({ name: 'Zildjian' });
kitty.save().then(() => console.log('meow'));
```

## 3 官方指南

### 3.1 设计Scheme发布Model

```javascript
const mongoose=require('mongoose')
const Schema = mongoose.Schema;
//连接数据库，若不存在则自动创建
mongoose.connect('mongodb://localhost:27017/test',{useNewUrlParser: true, useUnifiedTopology: true})
//设计文档结构（表结构）
//约束目的是为了保证数据的完整性，不要有脏数据

const userSchema=new Schema({
    username:{
        type:String,
        required:true
    },
    password:{
        type:String,
        required:true
    },
    email:{
        type:String
    }
})
//将文档结构发布为模型
const User=mongoose.model('User',userSchema)


```

### 3.2 增加数据

```javascript
let admin=new User({
    username:'admin',
    password:'123456',
    email:'admin@admin.com'
})

admin.save((err,ret)=>{
    if (err){
        console.log('保存失败')
    }else{
        console.log('保存成功')
        console.log(ret)
    }
})

```

### 3.3 查询

查询所有：

```javascript
User.find((err,ret)=>{
    if (err){
        console.log('查询失败')
    }else {
        console.log(ret)
    }
})
```

按条件查询所有：

```javascript
User.find({
    username:'liuzhang'
},(err,ret)=>{
    if (err){
        console.log('查询失败')
    }else {
        console.log(ret)
    }
})
```

按条件查询当个：

```javascript
User.findOne({
    username:'liuzhang'
},(err,ret)=>{
    if (err){
        console.log('查询失败')
    }else {
        console.log(ret)
    }
})
```

### 3.4 删除数据

```javascript
User.deleteOne({
    username: 'liuzhang1'
},(err,ret)=>{
    if (err){
        console.log('删除失败')
    }else {
        console.log('删除成功')
    }
})
```

### 3.5 更新数据

按条件更新所有：

```javas
User.updateMany({_id:'5edc916201de9f3344999a0f'},{password: '12312'},(err,ret)=>{
    if (err){
        console.log('更新失败')
    }else {
        console.log('更新成功')
    }
})
```

按条件更新所有查到的第一个：

```javascript
User.updateOne({_id:'5edc916201de9f3344999a0f'},{password: '12312'},(err,ret)=>{
    if (err){
        console.log('更新失败')
    }else {
        console.log('更新成功')
    }
})
```

