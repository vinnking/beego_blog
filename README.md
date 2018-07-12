beego_blog
====

Source: https://github.com/griffin702/beego_blog
myblog: http://www.inana.top/

默认不自动生成数据库，初次使用时可直接使用项目根目录下的beego_blog.sql手动导入数据库
初始管理员账号密码：admin 123456

感谢原作者：Double Liu

节点：
2018/6/19
1.0.0版本：
1、修复原项目代码中的BUG
2、优化整体逻辑及模型
3、更新新版bootstrap，优化PC与移动端自适应
4、页面整体优化

2018/7/10
1、新增评论模块，功能包括：登录评论，回复，引用，ajax无刷新提交，评论框自适应
2、继续完善所有模型，将原简单查询赋值改为高级联表外键查询
3、新增表查询频率很高的表索引，优化查询速度

2018/7/12
1、新增ipfilter模块
简介：该模块在某较大规模的服务端线上使用，同时经过多年测试改版积累，逻辑清晰简单，然而稳定性却非常好。
由于本站为个人站点性质，在整体框架不做改动的情况下，针对性改动算法规则，将该模块移植到本站。
功能：IP计数器、访问时间每10次更新1次，10次之间的访问时长进行算法对比，
目前算法为，每10次访问更新访问时间，并对比上次更新过的时间，间隔时长低于10s的被视为异常访问1次，
累计异常达到10次，则全站返回500，默认2分钟后计数器自动归零，目前测试比较稳定。
2、在ipfilter模块的基础上，实验型植入评论模块，规则仅做小小的修改，异常提交评论每次警告，当超过10次，
则全站会返回500，评论控制台则自然无法访问。
3、新增用户注册页面
4、评论列表访问时存在评论条数过大，从而导致表查询较慢，这个问题从两个方向着手处理
	a、优化orm，新增表索引，将所有条件查询的字段都加上索引，优化后，查询速度提升较高。
	b、评论列表分页显示，大大减少单页的查询次数。
5、修复部分敏感信息签名的bug