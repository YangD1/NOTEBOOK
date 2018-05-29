## laravel 使用速查

### 使用 `whereIn` 方法验证字段的值在指定的数组内
```
return User::whereIn('id',[1,2,3]);
```

### 使用 `with` 查询数据表中某个列数据 ，避免 N+1 查询
```
# 使用with查询
User::with('name')->get();

# 在with中指定查询某列字段
Post::with(array('user'=>function($query){
    $query->select('id','username');
}))->get();
```

### 在模型关联中取出指定的字段
```
public fuction()
{
    return $this->belongTo('User')->select(array('id','username'));
}
```

### 实现一些laravel的 Eloquent ORM 无法提供的查询
使用 [查询构造器](https://laravel-china.org/docs/laravel/5.5/queries/1327)

