# git 暂时忽略本地配置文件

在合作开发项目的时候，有些配置文件要根据各人的环境进行微调，而又不希望把这些修改 commit。使用 .gitingore 的粒度又不够，那样就把整个文件的更新都屏蔽掉了。

面对这种情况，可以使用如下方法配置

```sh
# 添加忽略文件
git update-index --assume-unchanged config.init

# 取消忽略
git update-index --no-assume-unchanged config.init

# 查看忽略了哪些
git ls-files -v | grep '^h'

# 批量取消
git ls-files -v|grep '^h' |awk '{print $2}' |xargs git update-index --no-assume-unchanged
```