# json-server使用教程

## 1 介绍

+ **json-server：**一个在前端本地运行，可以存储数据的server

+ **作用：**模拟接口，操作模拟数据

## 2 安装

```shell
npm install json-server -D
```

检查是否安装成功:

```shell
json-server -h
```

## 3 使用

创建 db.json文件：

```json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

运行：

```shell
json-server db.json
```

