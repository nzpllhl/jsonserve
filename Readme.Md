 ## jsonplaceholder.typiccode.com
 
 
 ## 一.获取所有用户的信息
 http://localhost:3000/users

## 二.获取个人用户信息
 http://localhost:300/users/1

## 四.获取所有公司
http://localhost:3000/companise/

## 四.获取id为1的公司信息
http://localhost:3000/companise/1

## 五.获取id为1的用户
http://localhost:3000/companise/1/users/

## 六.获取公司名字为MI的公司
http://localhost:3000/companise?name=Mi

## 六.获取多个公司 
http://localhost:3000/companise?name=Mi&name=Nuojy

## 七.获取一页中只有两条的数据
http://localhost:3000/companise?_page=1&_limit=2

## 八.升序排序 asc 升序 desc是降序
http://localhost:3000/companise?_sort=name&_order=asc

## 九.获取年龄18以及18以上的
http://localhost:3000/users?_age_get=18

## 十.获取年龄18-21之间的
http://localhost:3000/users?_age_get=18&_age_let=20 

## 自己伪造的数据
## Eaymoke

###  vuex中处理独立的模块 namespaced:true

## 让图片垂直居中
  ******vertical-align: middle;

## 点击搜索查询
```javascript
<input type="text" placeholder="搜索" v-model="filterValue"/>
data(){
  return{
    filterValue:"",
    customers:[],
  }
}
// v- for 循环的时候就不能单单的循环数据而是一个方法
v-for = "item in filterBy(customers,filterValue)",
methods:{
  filterBy(customers,value){
   return customers.filter((item)=>{
     return item.name.match(value);
   })
  }
}

```

## 改变数组内容的7种方法  
pop 删除的那一个
push  新的数组的长度
shift  删除的那一个
uhshift 新数组的长度
splice  返或被删除的项目
sort 排序后的数组
reverse 倒序后的数组
## 不改变原有数组
concat
slice
join
filter
forEach
map
some
revey

## vue 视图后台数据更新了，页面没有刷新！
vue 里页后台更新了但是页面数据没有个刷新，怎么解决
1.this.$set()
2.对象改变：oldObj = Object.assign({},newObj);
  原理：对象是引用类型，直接改变oldObj的某属性指向地址没变，vue不一定能监控到，
       所以当我们新建一个对象并赋值给oldObj字段的话，直接改变了它的指向地址
3this.$forceUpdate()，强制视图更新

## v-if 和 v-for 的优先级谁最高？
1. v-for 的优先级比v-if高,不可以同时使用

## 组件、插件 大全
## 克隆的组件 lodash
 1.npm i --save lodash 下载
 2.在需要用递归克隆的组件里引入组件
 import _ form 'lodash'

## 在全局挂载并且导入富文本编辑器https://www.jianshu.com/p/1675bcd396a2 
import VueQuillEditor from 'vue-quill-editor' 
import 'quill/dist/quill.snow.css' // 富文本编辑器外部引用样式  三种样式三选一引入即可引入样式
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.bubble.css'
import * as Quill from 'quill';
注册为全局可以使用的编辑器
Vue.use(VueQuillEditor)

## 路由懒加载
1、npm install --save-dev @babel/plugin-syntax-dynamic-import
下载好以后，在.babelsrc下配置
2、 "plugins": ["@babel/plugin-syntax-dynamic-import"]
3、之后在路由里配置
const home=>import('@/compontents/home/home')

 ## 路由权限控制
在客户端发送账号密码到服务端，服务端验证成功后返回token存储用户的权限，前端用Cookie把token存储在本地，在路由跳转(router.beforeEach)中判断是否存在token，另外前端可以通过token请求服务端获取userInfo，登录成功后在Vuex中存储着用户的信息(用户名，头像，注册时间等等)

权限控制
就是在路由跳转（router.beforEach）中判断token中的权限和要去往(to)页面的路由信息(router meta)中配置的权限是否匹配，同时我们的侧边栏也是根据权限动态生成的，当所登录的账号没有权限访问时，就不显示在侧边栏中（例如访客登录就无法看到编辑器的侧边栏选项），这样用户既看不到侧边栏选项，又无法直接访问到，双重控制更安全。

....
###  数据请求的时候get和set的区别
### GET /form.html?name=haha&&age=99
1. get 请求可以缓存保留在浏览器的历史记录中不安全 
2.     请求可以被收藏为书签
3.     请求长度有限制,这样就限定了GET方式不能做图片上传。
4.     请求只用于请回数据
5.     一般用于信息获取，使用 URL 传递参数，对所发送信息的数量也有限制，一般在 2000 个字符
### post http://localhost/form.html#
1. post 请求不会被缓存浏览器没有记录，比较安全
2.      请求体比较大,post把数据放在HTTP的包体内（requrest body）
3.      一般用于修改服务器上的资源，对所发送的信息没有限制 如：向服务器发送大量数据（POST 没有数据量限制）
....

### 请求码
1. 200 成功 
2. 204 表示成功但是后端还没有内容给你
3. 301 永久重定向
4. 302 临时重定向
5. 400 参数不当导致请求错误
6. 500 服务端内部数据错误
7. 404 客户端请求的资源或者数据不存在（一般是要么写错了接口，要么后端数据还没有部署）
 
## 讲一下ajax创建的4不
1. 创建一个XMLHttpRquerst 实例对象。也就是异步调用对象。 
2. 创建HTTP请求 并写上请求方法,接口，请求的参数URL即验证的信息。
3. 设置响应请求HTTP变化状态的函数
4. 发送HTTP
....
```javascript
let xhr = new XMLHttpRequest(); 
        xhr.open(get,'data.json')
        xhr.onreadystatechange = function(){
            if(xhr.onreadys === 4&&xhr.status ===200 ){
                console.log(data.responseTest);
            }
        }
        xhr.send()
```
## Vue 路由中有哪几种传参的方法？
1. 携带$router.push 编程式跳转 携带参数跳转 getList(item.id)
    很显然，需要在path中添加/:id来对应 $router.push 中path携带的参数。在子组件中可以使用来获取传递的参数值。
    getDescribe(id) {
   直接调用$router.push 实现携带参数的跳转
        this.$router.push({
          path: `/describe/${id}`,
        })

    this.$route.params.id
2. params
通过路由属性中name来匹配的路由，通过params来传递参数
   this.$router.push({
         name:'Describe',
         parmas:{
           id:id
         }
   })

  3. query 
   {
     path: '/describe',
     name: 'Describe',
     component: Describe
   }
....
....
## Cookie
1、cookie是由服务器生成发送给浏览器并保存在本地的一小块数据，
   它会在浏览器下次向同一服务器再次发起请求时，被携带并发送到服务器上。

2、依赖于登录后设置的Cookie，之后每次访问时都会携带该 Cookie，
   从而让后台服务能识别当前登录用户,可以从cookie拿到当前用户的全部信息。

*****注意:(Cookie和session是不可跨域的)
## session
1、从字面上讲就是会话，记录服务端与客户端的一种会话转态的机制。
2、session是基于cookie实现的，session是存储在服务器端的，sessionld会存储到用户端的cookie中

自己理解(
  第一次请求服务器的时候，服务器返回sessionID,
  第二次请求的时携带cookie中的sessionid服务器判断是属于哪个用户并执行后续的操作
  )

#### cookie和session的区别
1.安全性： Session 比 Cookie 安全，Session 是存储在服务器端的，Cookie 是存储在客户端的。
2.存取值的类型不同：Cookie 只支持存字符串数据，想要设置其他类型的数据，需要将其转换成字符串，Session 可以存任意数据类型。
3.有效期不同： Cookie 可设置为长时间保持，比如我们经常使用的默认登录功能，Session 一般失效时间较短，客户端关闭（默认情况下）或者 Session 超时都会失效。
4.存储大小不同:单个Cookie保存的数据不能超过4K，Session可存储数据远高于 Cookie但是当访问量过多，会占用过多的服务器资源。

## Acesss  Token
访问资源接口（API）时所需要的资源凭证
简单 token 的组成： uid(用户唯一的身份标识) time(当前时间的时间戳)、sign（签名:token 的前几位以哈希算法压缩成的一定长度的十六进制字符串）
特点：
服务端无状态化、可扩展性好
支持移动端设备
安全:
支持跨程序调用//绘画期间的存储机制服务端与客户端的一种会话机制
1.将登录成功后的token,保存到客户端的sessionStorage中，
  在项目中除了登录页面之外的，其他API都需要在登录之后才能访问
  token只在当前网站打开期间生效，所以将token保存在sessionStorage中
2.通过编程式导航跳到home
  window.sessionStorage.setItem('token',resp.data.token)
  登录成功之后跳到首页

## 为什么data里的属性必须是个函数
1. 因为组件是可以复用的,JS 里的对象是引用的关系。如果组件里的data是个对象，那么子组件里的data会污染，会产副作用。
2. 所以组件里的data必须是一个函数。保障自己数据的独立性。new Vue的实例不会被复用所以不存在以上问题。

## 说一说你对Vuex的理解
1. Vuex 是专门为vue.js 应用程序开发的转态管理模式。每一个Vuex的核心是store
2. store基本上可以说是一个仓库,管理vuex数据状态。
3. Vuex 里存储的数据是响应式的，当组件通过$stoer.state 获取state里的数据时，
   只要store中的数据发生变化那么组件内的数据也会得到 高效的更新。
4. 而想改变state里的数据，必须（commit）提交 mutions 才能修改state里的数据。这样才能方便我们跟踪每一步的数据变化。
5. astions 是异步的他对应的 

## vue里的路由
1. vue 的路由有三种模式 hash 模式  history模式 abstract 模式
 + hash 是使用 URL hash 的哈希做路由 。支持所有浏览器。
 + history 模式是支持 HTML5 History API 的服务器配置。
 + abstract 支持所有Javascript 运行的环境包括 Node 服务端，如果发现没有浏览器的API，路由会强制进入这个模式

 ## 
## 结合Element搭建搭建的后台管理系统
## 不明白的知识整理？
## 在布局的过程中，页面被拉小的时候页面不够会导致，元素挪到第二行，解决这个问题办法是给全局的html,body,app和设置一个最小宽度min-width:1366px;(解决页面宽度不够的时候会强制让那个页面宽度为1366px,这样就不会出现折行的问题)

### 处理Eslint的语法报错问题
> 在项目的根目录中创建一个文件.prettrerc是一个json格式的数据
{
  "semi":"false", 分号，
  "singleQuote":"true" //双引号

}

## 删除git多余的分支
我现在在login分支上，想删除login分支
　　1 、先切换到别的分支: git checkout login
　　2 、删除本地分支： git branch -d login
　　3 、如果删除不了可以强制删除，git branch -D login
　　4 、有必要的情况下，删除远程分支：git push origin --delete login
　　5 、在从公用的仓库fetch代码：git fetch origin login:login
　　6 、然后切换分支即可：git checkout login
　　注：上述操作是删除个人本地和个人远程分支，如果只删除个人本地，请忽略第4步

## 对git的整理
   1.在终端打开按CTRl + 、
   2.git branch 查看当前分支
   3.git checkout master 切换到当前主分支上
   4.先把当前分支合并到主分支上，git merge login
   5.把本地的代码推送到码云中
## 把本地的分子推送到云端，进行保存
   1.首先通过git checkout login切换到子分支上
   2.如果云端没有login子分支的话，直接push是推送不成功的
   3.要操作git push -u origin login 这句话的意思是要把本地的代码子分支推送到远程的login分支上
注意的点：写的原代码发现测试没问题，要合并到主分支推送到远程仓库中，还要把子分支也一定推送到子分支的远程仓库中。

## git checkout -d user 新建一个user并且切换到user分支上
   1.git add .
   2.git commit -m '完成用户列表功能的开发'
   3.git push -u origin users 这句话的意思是要把本地的代码子分支推送到远程的users分支上
   4.git mage master 

## git checkout -b rights创建一个用户权限的子分支。
   1.git push -u origin rights 这句话的意思是要把本地的代码子分支推送到远程的rights分支上

## 通过接口获取数据
main.js里 挂载在原型之前axios 请求拦截器添加token,预处理的过程
````
axios.interceptors.request.use(config=>{
    为请求头对象增加token验证的Authorization字段
    config.headers.Authorization= window.sessionStorage.getItem('token')
    return config
})
````

## 通过路由导航控制页面的登录效验==路由导航首位 router.deforeEach
>  在全局首位只要页面的路由发生变化，就会触发的函数
````
router.deforeEach((to,from,next)=>{
  //如果路径是的路由页面那就直接发行，因为登录页面不不用效验
  if(to.path==='/login') return next()
  //从window。seassionStorage中获取一下看看token有没有，或者是有没有过期
  如果没有那证明没录登录过返回登录中心重新登录
  const tokenStr = window.sessionStorage.setItem('token')
  if(!tokenStr) return next('/login')
  next()

})

对于全局后置钩子：要离开的钩子，没有next()
router.afterEach((to, from) => {
    // do someting
});

````

## 组件内的导航钩子有三个
````
1.路由进入之前
beforeRouteEnter(to, from, next) {
    next (vm => {
        // 这里通过 vm 来访问组件实例解决了没有 this 的问题
    })
}

需要注意是：
beforeRouteEnter 不能获取组件实例 this，因为当守卫执行前，组件实例被没有被创建出来，剩下两个钩子则可以正常获取组件实例 this
const File = {
    template: `<div>This is file</div>`,
    beforeRouteEnter(to, from, next) {
          next(vm=>{
            vm获取实例this
          })
         do someting
         在渲染该组件的对应路由被 confirm 前调用
    },
    beforeRouteUpdate(to, from, next) {
         do someting
         在当前路由改变，但是依然渲染该组件是调用
    },
    beforeRouteLeave(to, from ,next) {
         do someting
         导航离开该组件的对应路由时被调用
    }
}


````

## 1、完成登录功能：
````
<el-form :model="LoginForm" :rules="Loigrules" ref="LoigfromRes" label-width="100px" class="demo-ruleForm">
  <el-form-item label=用户名" prop="username">
    <el-input v-model="LoginForm.username"></el-input>
  </el-form-item>
  <el-form-item label="密码" prop="passord" type="passord">
    <el-input v-model="LoginForm.passord"></el-input>
  </el-form-item>
   <el-form-item >
    <el-button type="primary" @click="goLogin">登录</el-button>
    <el-button type="info" @click="restLoigFrom">重置</el-button>
  </el-form-item >
  </el-form>

data(){
  return{
    LoginForm:{
      username:"",
      passord:""
    }
  },
  Loigrules:{
    username:[
       { required: true, message: '请输入用户名', trigger: 'blur' },
       { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
    ],
    porssow:[
       { required: true, message: '请输入密码', trigger: 'blur' },
      { min: 3, max: 6, message: '长度在 3 到 6 个字符', trigger: 'blur' }
    ],
}
}
methods:{
  //点击的时候重置表单
  restLoigFrom(){
  this.$refs.LoigfromRes.restFields()
  },
  //登录的时候进行验证
  goLogin(){
    //登录之前发起求，调用表单的实例
     this.$refs.LoigfromRes.validate( async valid=>{
       if (!validate) return ; 
       let {data:resp} = await this.$axios.get('/long',this.LoginForm)
         if(resp.meta.status !==200) return utlis.altre('resp.msg') //失败
         utlis.altre('resp.msg') //成功
         1.将登录成功后的token,保存到客户端的sessionStorage中，//绘画期间的存储机制
           在项目中除了登录页面之外的，其他API都需要在登录之后才能访问
           token只在当前网站打开期间生效，所以将token保存在sessionStorage中
         2.通过编程式导航跳到home
           window.sessionStorage.setItem('token',resp.data.token)
         //登录成功之后跳到首页
         this.$router.push('/home')

        }
       }
     })
  }
},
created:{},
````
## 2、完成退出登录功能
````
点击退按钮的时候清空sessionStorage里的token
logaut(){
  window.sessionStorage.clear()
  this.$router.push('/login')
}

````
## 3、获取导航的菜单数据：
1.在页面一加载的时候获取数据，没有参数所以直接获取。
2.获取到数据后通过双for循环，循环展示数据meunList
数组中的每一项都是一级菜单，每一项里的childer数据是二级菜单
````
    data(){
        return{
            iconsObject:{
                'id':'图标'，
                '123'："el-icon-s-check"
                '302':""el-icon-s-check"
                '303':"el-icon-s-check"
            }，
            isCollapse:false //默认不折叠
            activePath:'' //别激活的链接路由地址
        }
    },
    created(){
        //页面一加载的时候获取一下
        this.activePath = window.sessionStorage.getItem('activePath')
    }
    methods:{
    toggleCollapse(){
     this.isCollapse = !this.isCollapse
    },
    //点击二级菜单的时候，保存当前的状态
    saveNavState(activePath){
     window.sessionStorage.setItem('activePath',activePath)
     this.activePath = activePath
    }
    }

    <el-aside :width:"isCollapse ? '64px':'200px'">
    <el-menu
      :default-active="activePath"
      background-color="#333744"
      text-color="#fff"
      active-text-color="#ffde44" //激活的文本颜色
      unique-opened
      :collapse = "isCollapse" //默认不折叠
      router //路由

     >
     一级菜单
      <el-submenu :index="item.id +''" v-for="item in meunList" :key="item.id">
        <template slot="title">
          <i :class="iconsObject[item.id]"></i>
          <span>{{item.autName}}</span>
        </template>
        二级菜单
        <el-menu-item :index="'/'+subitem.path" v-fo="subitem in item.children" :key="subitem.id" @click="saveNavState('/'+subitem.activePath)">
          <template slot="title">分组一</template>
            <i class="el-icon-location"></i>
           <span >{{subitem.autName}}</span>
        </el-menu-item-group>
      </el-menu-item
    </el-menu>
 </el-aside>
````
3.修改一级菜单的图标，在自动for循环的时候，渲染自定义的图标
  3.1在data中定义一个自己的自定义图标
4.每次只展一个，如果是点开一个，那其他的就默认收起来 unique-opened =>boolean
5.控制菜单的折叠展开：绑定点击事件@toggleCollapse切换菜单的折叠与展开collapse
6.写样式的时候:居中text-align:center,间距:letter-spacing:0.5rem 小手：cursor:pointer
8.要让侧边栏通过显示与影藏展示对应的样式而不是写死

## 4、首页路由的重定向
1.定义一个重定向的组件，登录成功后访问的是home页，但是默认重定向到了welcome.vue组件中
````
routes:[
    {
        path:'/home',
        compontent:'/home',
        redierct:'welcome'
        childer:[
            {
                path:'/welcome',
                compontent:'welcome'
            }
        ]
    }
    {}
]
````

## 5、用户管理实现分页效果
请求的时候要把全选的数据页码参数带过去
````
 <el-pagination
      @size-change="handleSizeChange" // 最新的每页条数pageSize
      @current-change="handleCurrentChange" //最新的页码值pageNum
      :current-page="queryInfo.pagenum" //当前显示的是第几页的数据
      :page-sizes="[1, 2, 3, 4]"
      :page-size="queryInfo.pagesize"
      layout="total, sizes, prev, pager, next, jumper"
      :total="400">
    </el-pagination>
data(){
    return{
    queryInfo：{
    query:''
    pageSize：1 //当前每页显示多少条数据
    pageNum：2 //当前的页数
    }
    total:0
    }
},
methods:{
    //当前显示多少条
    handleSizeChange(newSize){
     this.queryInfo.pagesize = newSize
    //调用获取用户列表的数据方法
      this.getUserList()
    },
    //监听页码值改变的数据
    handleCurrentChange(newPage){
    this.queryInfo.pagenum = newPage
    this.getUserList()
    }
}

````
## 实现数据搜索功能
1.点击思索的时候，通过调用获取数据的方法查询
````
<el-input
  placeholder="请输入内容"
  v-model="queryInfo.query"
  clearable
  @clear="getUserList"//清空所有的搜索功能的实现
  >
  <el-button @click="getUserList()">搜索</el-button>
</el-input>
````
## 用户列表删除用户msgbox
````
<template slot-scope="scope"
<el-button @click="removeUserId(scope.row.id)"></el-button>
</template>
data(){
    return{

    }
},
methods:{
    根据ID删除用户信息
   async = removeUserId(id){
    const confrmResult= await this.$confirm('此操作将永久删除该用户, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).catch(err=> err)
    }
    log(confrmResult)
    如果用户确认删除，返回值为字符串confirm
    如果用户确认不删除，返回值为字符串catch
    if(confrmResult!=='confirm'){
        return this.$messaage.info('已经取消删除')
    }
    const {data:res}this.axios.delete("users/" + id ){
        if(res.met.status !==200){
            return this.$message.error('删除用户失效！')
        }
        this.$message.sucess('删除用户成功！')
       thi.setUserList() 删除完后重新调用获取数据的方法
    }

}
````

## 5.用户列表完成分配角功能
1.点击分配 展现出，分配角色的对话框。
````
<el-dialog
  title="分配角色"
  :visible.sync="setDialogVisible"
  width="30%"
 >
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </span>
</el-dialog>
````
## 6、用户权限的业务逻辑分析
1.通过权限管理模块控制不同的用户可以进行的操作，具体可以通过角色的方式进行控制，即每个用户分配一个特定的角色
  角色包括不同的功能权限。
2.简单理解就是，不同的账号是不同的角色，不同的角色有不同的功能。

## 7、用户列表
````
data(){
    return{
    userList:[]
    }
},
created(){
    this.getUserList()
}
methods:{
  //获取用户列表的数据
 asyns getUserList(){
let {data:resp} = await this.$axios.get('userList'+list)
.then((resp)=>{
  this.userlist = resp.data
})
}

}
卡片视图
<el-card class="box-card">
   <el-table
    :data="userList"
    border
    style="width: 100%">
    <el-table-column
      prop="uaerName"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="path"
      label="路径"
      width="180">
    </el-table-column>
    <el-table-column
      prop="px"
      label="权限">
<template slot-scope="scope">
      <el-tag type="info" v-if="scope.row.level===0">一级</el-tag>
     <el-tag type="warning" v-else-if="scope.row.level===1">二级</el-tag>
     <el-tag type="danger" v-else>三级</el-tag>
 </template>

    </el-table-column>
</el-card>

````
## 8、角色列表的创建。
1.基础布局
  复制之前的面包屑
2.角色列表没有参数直接获取list
3.closable tag里的X
````
<el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
<el-breadcrumb-item><a href="/">加色列表</a></el-breadcrumb-item>
<el-breadcrumb-item></el-breadcrumb-item>
<el-card class="box-card">
   <el-table
    :data="roleList"
    border
    style="width: 100%">
    ***展开列 > 用作作用域插槽获取对应的角色信息，然后通过三层for循环拿到对应的信息
     <el-table-column type="expand"> 展开 <
      <template slot-scope="scope"> 
        要放一个栅格系统的布局组件
        ## 角色下权限的渲染
          如果这行的索引为0就给加一个底边框，不为0就不加
         <el-row :class="['bdbottom',i1===0?'bdtop':'','vcenter']"v-for="(item1 i1) in scope.row.children" :key="item1.id">所有权限的一级数组
        渲染一级权限占5列
           <el-col :span="5">
           <el-tag  @close="ReomveByid(scope.row.item1.id)>{{item1.authName}}</el-tag>
           <i class="el-icon-edit"></i>
           </el-col>
        渲染二级三级级权限
           <el-col :span="19">
            <el-row :class="[i2 === 0? '':'bdtop','vcenter']" v-for="(item2 i2) in item1.children" :key="item2.id">
            <el-col :span="6"><el-tag type="sucsec" @close="ReomveByid(scope.row.item2.id)>{{item2.authName}}</el-tag></el-col>
            <el-col :span="18">
        三级级权限
               <el-tag type="黄色" v-for="(item2 i3) in item2.children" :key="item3.id" closable @close="ReomveByid(scope.row.item3.id)">{{item3.authName}}</el-tag>
            </el-col>
            </el-row>
            </el-col>
         </el-row>
      </template>
     </el-table-column> 
    <el-table-column type="index"></el-table-column>
    <el-table-column
      prop="uaerName"
      label="角色名称"
      width="180">
    </el-table-column>
    <el-table-column
      prop="path"
      label="角色描述"
      width="180">
    </el-table-column>
    <el-table-column
      prop="px"
      label="操作">
<template slot-scope="scope">
  <el-button type="primary" size="mini" disabled>编辑</el-button>
  <el-button type="success" size="mini" disabled>删除</el-button>
  <el-button type="info" size="mini" disabled>分配权限</el-button>
 </template>
</el-table-column>
</el-card>
data(){
  return {
     
  },
  methods:{
  根据ID点击删除按钮退出确认提示框
   async ReomveByid(row,rigthid){
    const confirmRusul = await  this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).catch(err=>err)
        })
        //证明用户不想删除
        if(confirmRusul ！=== 'confirm'){
           return this.$message.info('取消了删除！')
        }
     const {data:res}  =  await this.$axios.delete(`roles/${row.id}/rights/${rigthid}`)
      if(res.mast.status !===200) return this.$message.error('删除权限失败！')
    }  
      为当前的三级权限信息赋值
      role.cchildren = res.data
        
  }
}

````
style
在上边宽和边宽不好设定的情况下，动态设置
.bdtop{
  boeder-top:1px solid pink
}
.bdtottom{
  border=bottom:1px solid pink
}
让元素居中
.vcenter{
  display:flex,
  align-items:center;
}

## 9、树形菜单的使用分配权限列表 MD
````
<el-tree
ref="treeRef"
:data = "RolesList" 获取过来的数据源
:props:"treeProps" 数据的关键字
show-checkbox 
node-key = "id" 获取勾选对应节点的ID,只要选中对应的节点那么选中的就是对应的ID
default-expand-all 是否展开全部树
:default-checked-keys="defkeys"默认勾选节点的权限的数组[]
1.思路在点击分配权限的时候获取默认钩选的数据ID
2.把半选和全选的id拼在一起
></el-tree>
data(){
  return{
    roleId:'' //点开分配权限的时候就获取id showSetRightDialog(role){this.roleIdc = role.id}
    treeProps:{
    children:'children' 父子通过属性绑定在一起
    ladel:'label'
} 
defKeys:[],
  }
},
methods:{
//展示分配权限的对话框
  showSetRightDialog(role){
    this.roleIdc = role.id
获取树的数据：
asyns getRolesList(){
let {data:resp} = await this.$axios.get('RolesList/tree')
.then((resp)=>{
   
   this.RolesList = resp.data //获取到的权限数据
   //获取完数据后调用递归,role这里是直接拿不到的，要在点击分配权限的方法里传（scope.row）
    this.gitlefdefKeys(role,this.defKeys)//这样三级权限的默认选中也就有了  this.setRightDilgVisible = true
})
}
  } 
//递归获取3级节点的ID获取默认节点的id,并保存到数组defKey中
  gitlefdefKeys(node,arr){
//如果这个节点的ID不包含children没有孩子就证明，是3级权限节点
  就把每一个没有孩子的idpush到数组中
   if(!node.children){
    rerturn arr.puah(node.id)
   }
   //递归拿到是所有孩子的id
   node.children.forEach(item=>{
    gitlefdefKeys(item,arr)
   })
  },
  //监听对话框的关闭事件,防止出现重复的id
  setRighDialogtClose(){
    this.defKeys=[]
  }

}
解决一个bug:
1.每次关闭对话框的时候清空一下数组里的元素项
2.监听对话框的处理函数：@close="setRightClosed"
点击确定为分配权限，把默认的角色拼接在一起统一发过去取
addotRights(){ 
  const keys = [
    ...this.$refs.treeRef.this.getCheckedKeys(),
    ...this.$refs.treeRef.this.getHalfCheckedNodes(),
  ]
  const idStr = keys.join(',')
  this.$axios.post(`rolse/${this.roleId}/rights`,{rids:idStr})
}

````
## 10、点击分配角色完成分配权限的功能setRole(scope.row) 当前这一行的用户的信息
````
<el-dialog
  title="分配角色"
  :visible.sync="setRoledialogVisible"
  width="50%"
  >
 <div>
  <p>当前的用户:{{userinfo:userName}}</p>
   <p>当前的角色:{{userinfo:role_name}}</p>
   下拉菜单
   <p>
   分配新角色：下拉框
    <el-select v-model="selectedRoleId" placeholder="请选择">
    <el-option
      v-for="item in rolesList"
      :key="item.id"
      :label="item.roleName"
      :value="item.id">
    </el-option>
  </el-select>
   
   </p>
 </div>
  <span slot="footer" class="dialog-footer">
    <el-button @click="setRoledialogVisible= false">取 消</el-button>
    <el-button type="primary" @click="saveRoleinfo">确 定</el-button>
  </span>
</el-dialog>

data(){
  return{
    setRoledialogVisible :false,
    userinfo:{} 需要被分配角色的用户对象
    rolesList:[],
    已选中的角色id值
    selectedRoleId:''

  },
  methods:{
   async setRole(userinfo){
      this.userinfo = userinfo
      //展示对话框之前获取数据下拉列表的数据
    const {data:rea} = await this.$axios.get('roles')
    if(res.mate.statue !== 200) {
      return this.$message.err('获取角色列表失败！')
    }
    this.rolesList = res.data
      this.setRoledialogVisible = true
    },
    点击确定的时候,把分配的角色
  asyns  saveRoleinfo(){
      如果没有选择要分配的权限，那么提醒用户请选择要分配的角色
     if(!this.selectedRoleId) {
      return this.$message.ree('选择要分配的角色!')
     }
    const {data:res} = await this.$axios.put('user/${this.unseinfo.id},{rid:this.selectedRoleId}')
    }
    if(res.mast.statue !== 200){ return this.$massage.err('用户角色更新失败！')
    }
    this.$message.success('更新角色成功！')
    thi.getUserList()
    
  }
}

开发过后的代码推送到云端:先把代码提交到自己的分支，切换到主分支上也同样要push
````
###  11第三大模块分类管理的开发
> git branch 
> git checkout -b goods——cate
> git push -u origin goods——cate
分类管理这里的树形Element实现不了，使用另外的插件vue-table-with-tree-grid
https://github.com/MisterTaki/vue-table-with-tree-grid
````
面包屑
<temple>
<el-breadcrumb separator="/">
  <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
  <el-breadcrumb-item><a href="/"></a>商品管理</el-breadcrumb-item>
  <el-breadcrumb-item>商品分类</el-breadcrumb-item>
</el-breadcrumb>
卡片视图区域
<el-card>
<el-row class='cat_opt'> 行
 <el-col>
  <el-button type="蓝色" @click="showAddCateDialog">添加分类</el-button>
 </el-col>列
</el-row>
tree属性表格：columns表格列的配置
:selection-type="false" 隐藏前面的复选框
:expand-type="false" 前面的住展开行
<tree-table :data="cateList" :columns="columns" 
:selection-type="false" :expand-type="false" show-index :index-text="#" border>
// 插槽渲染是否有效和图标
<template slot="isok" slot-scope="scope">
<i class="el-icon-circle-check" v-if="scope.row.cat_delete === false"></i>
<i class="el-icon-error" v-else></i>
</template>
//排序
<template slot="order" slot-scope="scope">
 <el-tag size="mini" v-if="scope.row.cat_level===0">一级</el-tag>
 <el-tag size="mini" type="success" v-else-if="scope.row.cat_level===1"二级</el-tag>
 <el-tag size="mini" type="success" v-else>三级</el-tag>
</template>
//操作
<template slot="opt" slot-scope="scope">
<el-button type="primary" icon="el-icon-edit" size="mini">编辑</el_button>
<el-button type="danger" icon="el-icon-dlete" size="mini">删除</el_button>
</template>
</tree-table>
//分页效果
 <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page.sync="currentPage2"
      :page-sizes="[3, 5,10,15]"
      :page-size="queryinfo.pagesize"
      layout="sizes, prev, pager, next"
      :total="total">
    </el-pagination>
</el-card>
<!-- 添加分类的对话框 -->
<el-dialog
  title="添加分类"
  :visible.sync="addCatedialogVisible"
  width="50%"
  @close="addCateDialogClosed"
  >
  <!-- 添加分类的表当 -->
  <el-form :model="addCartruleForm" :rules="addCartrules" ref="rulrefeForm" label-width="100px" addCartruleFormclass="demo-ruleForm">
  <el-form-item label="分类名称：" prop="addCartruleForm.cat_name">
    <el-input v-model="addCartruleForm.cat_name"></addCartruleFormel-input>
  </el-form-item>
    <el-form-item label="父级分类：" prop="addCartruleForm.cat_pid">
    <!-- options 接连选择器知道数据源联级菜单-->
    <el-cascader
    v-model="selectKyes"
    :options="parentCateList"
    expand-trigger = 'hover'
    :props="cascaderProps"
    @change="ParentCateChange"
    clearable  清空的功能
    change-on-select 如果想要选中任意一级分类增加的属性
    >
    </el-cascader>
  </el-form-item>
  </el-form>
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false" @click="addCat">确 定</el-button>
  </span>
</el-dialog>
</temple>
data(){
  return{
    查询条件
    querinfo:{
     type:3,
     pageName:1,
     pageSize:5
     
    }
    total:0,总数据台数
    cateList:[], 商品分类的数据列表
    parentCateList:[] 父级分类的数据
     columns:[
      {
        label:"分类名称",
        prop："cat_name",
      },
      {
        label:'是否有效',
        type:'template', 表示将当前列表定义为模板列
        template:'isok' 

      },
      {
        label:'排序',
        type:'template', 表示将当前列表定义为模板列
        template:'order' 

      },
      {
        label:'操作',
        type:'template', 表示将当前列表定义为模板列
        template:'opt' 

      },
      ],
   addCatedialogVisible:false; 控制添加分类对话框的显示
   addCartruleForm:{
     cat_name:''    
     cat_pid:0 父级分类的id
     cat_level：1 默认要添加的一级分类

   }, 添加分类的表单数据对象
   addCartrrules:{效验规则对象
       cat_name:[
         { required: true, message: '请输入分类规则的名称', trigger: 'blur' },
       ]

   },
    指定接连菜单的对象
    cascaderProps:{
      value：'cat_id',
      label:'cat_name',
      children:'children'
    },
    选中的父级分类数组
    selectKyes:[]
    },
    隐藏
    created:{
    this.getCateList()

  }
  methods:{
 获取商品分类列表的数据
async getCateList(){
  const {data:res} =  await this.$axios.get('categorise',{params:this.querinfo})
  if(res.meta.staus !== 200) {
    return this.$message.error('获取商品分类失败！')
  }
  this.catelist = res.data.result
  this.total =  res.data.total

 },
 handleSizeChange(newSize){
   this.queryinfo.pagesize = newSize
   this.getCateList()
 },
 handleCurrentChange(newName){
  this.queryinfo.pagename = newName
   this.getCateList()
 },
 //点击弹出对话框
 showAddCateDialog(){
   点开对话框之前获取父级分类的数据
   this.getParentCateList() 
  this.addCatedialogVisible = true 
 },
 //获取父级分类的数据列表,获取父级数据分类的时候最多分两级 
 getParentCateList(){
   this.$axios.get('categories',{params:{type:2}})
   if(res.meta.statue !== 200){
      return this.$message.error('获取父级分类数据失败！')
   }
    this.parentCateList = rea.data 获取到数据
   },
   只要联级菜单发生变化选择项发生变化触发的函数
   ParentCateChange(){
     this.selecctKyes 选中的值双向绑定到data中
     如果this.selectKyes里的长度大于0那就代表选中了父级分类，反之就没有选中任何分类
     if(this.selectKyes.length > 0){
      this.addCateFrom.cat_pid =  [this.selectKey.length-1]
     }
     //为当前分类的等级赋值
     this.addCateForm.cat_level = this.selectKey.length
     return
   }else{
     //没有选中分类就直接赋值为0
    this.addCateFrom.cat_pid = 0
    this.addCateForm.cat_level = 0
   },
   
   点击确定的时候调用接口
   addCat(){
   this.$ref.rulrefeForm.validate(( async valid)=>{
     if(! valid) return
    let {data"res } = await this.$axios.post('categries',this.addCartruleForm)
     if(res.mate.status !== 200){
        return this.$message.error('添加分类失败！')
     }
     this.$message.success('添加分类成功！')
   })
   
   },
   监听对话框的关闭事件，重置表当所有数据
   addCateDialogClosed(){
    this.$refs.rulrefeForm.resetFields()
    this.selectKey = [],
    this.addCateForm.cat_level = 0
    this.addCateFrom.cat_pid = 0
   }
  },

  
}
````
最后把已经完成的商品分类提交到远程仓库
> git branch 
> git status
> git add .
> git commit -m '完成商品分类'
> git push   推送到云端的分支
> git checkout master 切换到主分支
> git merage goods_cat 合并主分支的代码
> git push


## 第四个大模块分类参的开发
> git branch
> git checkout -b goods_params
> git push -u origin goods_paeams 
> 基于这个分支开发
> 什么是商品分类？
商品参数用于显示商品的固定特征信息，可以通过电商平台商品详情页面直观的看到 
> 动态的参数和静态的属性
> 动态参数是在用户选择商品的时候动态供用户选择自己喜欢的商品
> 静态参数是只读的用户只能看到商品对应的数据信息不可以选择或者修改（只能查看商品的对应信息）

创建组件页面

````
<template>
 <div>
<!-- 面包屑 -->
 <el-breadcrumb separator-class="el-icon-arrow-right">
  <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
  <el-breadcrumb-item>商品管理</el-breadcrumb-item>
  <el-breadcrumb-item>参数列表</el-breadcrumb-item>
</el-breadcrumb>
<!-- 卡片视图区-->
<el-card>
<!-- 头部的警告区 -->
<el-alert 
    title="注意：只能允许为三级的分类设置相关参数！" type="warning"
    type="info"
    effect="dark"
    :closable="false"
    show-icon
    >
  </el-alert>
  <!-- 选择商品分类区 -->
  <el-row>
   <el-col>
     <span>
       选择商品分类：
       <!-- 联动选择框 -->
  <el-cascader
    v-model="CateselectKeys" 联动菜单中选中id集合
    :options="CartList" 数据源  
    :props="cateProps" 对象 
    expand-trigger = 'hove'
    @change="handleChange"></el-cascader>
     </span>
   </el-col>
  </el-row>
<!-- tab页签区域 -->
    <el-tabs v-model="activeName" @tab-click="handleTabClick">
   <!-- 添加动态参数的面板 -->
    <el-tab-pane label="动态参数" name="many">
    <el-button type='primary' size="mini" :disabled="isBtnDisabled" @click="adddialogVisible = true">添加参数</el-button>
    <!-- 动态参数表格渲染-->
    <el-table>
    <!-- expand 展开列 -->
     <el-table-column type="expand"></el-table-column>
      <el-table-column type="index"></el-table-column>
      <el-table-column label="参数名称" prop="arrt_name"></el-table-column>
      <el-table-column label="操作">
        <template slot-scope="scope">
        <el-button type="primary" icon="el-icon-search"size="main" @click="showEditDialog(scope.row.attr_id)">编辑</el-button>
         <el-button type="danger" size="main" icon="el-icon-edit" @click="remove(scope.row.attr_id)>删除</el-button>
        </template>
      </el-table-column>
    <el-table/>
    </el-tab-pane>
    <!-- 添加静态参数的面板 -->
    <el-tab-pane label="静态属性" name="only">  <el-button type='primary'
     size="mini"
     :disabled="isBtnDisabled" @click="adddialogVisible = true">添加参数</el-button>
       <el-table>
    <!-- expand 展开列 -->
     <el-table-column type="expand"> 
     <!-- 展开列下的版式 -->
      <template slot-scope="scope">
         <el-tag v-for="(val, i) in scope.row.attr_vals" closable @close="handeClose(i，scope.row)">{{val}}</el-tag>
         <!-- s输入文本框 -->
      <el-input
          class="input-new-tag"
          v-if="scope.row.inputVisible"
          v-model="scope.row.inputValue"
          ref="saveTagInput"
          size="small"
          @keyup.enter.native="handleInputConfirm(scope.row)"
          @blur="handleInputConfirm(scope.row)"
       >
     </el-input>
     <!-- 添加tag的按钮 -->
<el-button v-else class="button-new-tag" size="small" @click="showInput(scope.row)">+ New Tag</el-button>
</template>
     </el-table-column>
      <el-table-column type="index"></el-table-column>
      <el-table-column label="属性名称" prop="arrt_name"></el-table-column>
      <el-table-column label="操作">
        <template slot-scope="scope">
        <el-button type="primary" icon="el-icon-search"size="main" @click="showEditDialog(scope.row.attr_id)">编辑</el-button>
         <el-button type="danger" size="main" icon="el-icon-edit" @click="remove(scope.row.attr_id)">删除</el-button>
        </template>
      </el-table-column>
    <el-table/>
    </el-tab-pane>
  </el-tabs>
</el-card>

<!-- 添加参数的对话框静态参数和动态参数共用一个对话框-->
<el-dialog
  :title="'添加'+ titleText"
  :visible.sync="adddialogVisible"
  width="50%"
  @close=""
  :before-close="handleClose" addDialogClosed
  <!-- 添加参数的对话框 -->
  <el-form :model="addForm" :rules="addFromrules" ref="addruleFormref" label-width="100px" >
  <el-form-item :label="titleText" prop="attr_name">
    <el-input v-model="addForm.attr_name"></el-input>
  </el-form-item>
  </el-from>
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="addParams">确 定</el-button>
  </span>
</el-dialog>

<!-- 修改参数的对话框 -->
<el-dialog
  :title="'修改'+ titleText"
  :visible.sync="editialogVisible"
  width="50%"
  @close=""
  :before-close="handleClose" @close='editDialogClosed'
  <!-- 添加参数的对话框 -->
  <el-form :model="editForm" :rules="editFromrules" ref="editruleFormref" label-width="100px" >
  <el-form-item :label="titleText" prop="attr_name">
    <el-input v-model="addForm.attr_name"></el-input>
  </el-form-item>
  </el-from>
  <span slot="footer" class="dialog-footer">
    <el-button @click="editdialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="editParams">确 定</el-button>
  </span>
</el-dialog>
 </div>
</template>
<script>
export default{
  data(){
    return{
    CartList:[]
    },
    配置联级选择框的对象
    cateProps:{
      value:'cat_id',
      lable:'cat_name',
      children:'children'
    }
  },
   
  联动选择框双向绑定的数据
  CateselectKeys:[],
  activeName:"many", 被激活的页签名
  manyTableDate:[] many 动态数据
  onlyTabName:[] only 静态属性的数据
  addialogVisible:false 控制添加对话框的显示隐藏
  addForm:{          添加参数的表单对象
   attr_name:''
  },
addFromrules:{添加参数的表单效验对象
 attr_name：[
  {required:true,message:'请输入参数名称',trigger:'blur'}
 ]
},
修改参数
editialogVisible:false,
editFromrules:{
  attr_name：[
  {required:true,message:'请输入参数名称',trigger:'blur'}
 ]
},
editForm:{
  attr_name：''
}, 修改的表单


}, 

  methods:{
   获取所有商品分类的数据
   asyns getCatLsit(){
   const {data: res} = awai this.$axios.get('Categoners')
   if(rea.data.status !== 200) return this.message.error('获取商品参数列表失败！')
    this.CartList = data.res
   },
   监听联动选择框的函数
    handleChange(){
     this.getparamsDate()
    },
   //获取参数的列表数据
   asyns getparamsDate(){
    如果this.CateselectKeys.length !==3,那就代表选中的不是三级分类
     if(this.CateselectKeys.length !==3) {
       this.CateselectKeys = []
       this.manyTableDate = []
       this.onlyTableDAte = []
       return 
     } 
     根据所选分类的ID和当前的所处的面板，获取对应的参数
    const {data:res} = this.$axios.get(`categories/${this.catId}`,{params:{sel:this.activeName}}
    if(res.meta !==200){
       return this.$message.reeor('获取参数列表数据失败')
    }

     在赋值之前把每一项里面的attr_values修改成数组，方便tag表格的渲染
     res.data.forEach((item)=>{
    //判断一下item.attr_vals是否为空？不为空就切，为空就返回数组
       item.attr_vals = item.attr_vals ? item.attr_vals.split(' '):[]
       控制文本框的显示与隐藏
       item.inputValue = false
       控制文本框中输入的值
       item.inputValue = ''
     })

     因为获取过来的时候不知道是动态mary的还是静态only属性，所以获取过来后做一个判断
     if(this.activeName === 'mary'){
         this.manyTableDate = res.data
     }else{
       this.onlyTabName = res.data
     }
   },
  Tab页签点击事件activeName函数
   handleTabClick(){
     this.getparamsDate()
   },
  监听添加对话框的关闭事件
   addDialogClosed(){
   this.$refs.addruleFormref.refstField()
   },
  点击按钮，添加参数
   addParams(){
     this.$refs.addruleFormref.validate(async (valid)=>{
     if(!valid) return
   const {date"res} =await this.$axios.post(`categories/${this.cateId}/attributes`,{
       attr_name:this.addFrom.attr_name,
       attr_sel:this.activeName
     })
     if(res.mate !==200) {
       return this.$message.reeor('增加商品失败！')
     }
    this.$message.reeor('增加商品成功！')
    this.adddialogVisible:false
    this.getparamsDate()
     )
     })
   },
   点击按钮展示修改的对话框
  async showEditDialog(attr_id){
   const {data:res = await this.$axios.get(`categories/${this.cateId}/attributes/${attr_id}`,params:{attr_sel:this.activName})
   editialogVisible:true
   },
   editDialogClosed(){
     this.$refs.edi.ruleFormref.resftField()
   }
   //点击按钮修改参数信息
   async editParams(){
   this.$refs.editruleFormref.validdate((valid){
     if(!valid) return 
   const {data:res} = await  this.axios.put(`categories/${this.cateId}/${this.editForm.attr_id}`,{attr_name:this.addFrom.attr_name,attr_sel:this.activeName})
   })
   if(res.mate.status !==200){
     return this.$messsge.error('修改参数失败！')
   }
   this.$message.sucess('修改数据成功！')
   this.getParamsDate()
   this.eidialogVisible:false
   } 
 
 //点击根据ID删除
asyns remove(attr_id){
 const confirmResult =await this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).catch(err=>err)
        用户取消了删除的操作
        if(confirmResult !== 'confirm'){
          return this.$message.info('已取消删除！')
        }
  //不去取消就掉用接口
 const {data:res} this.$axios.delete(`categories/${this.cateId}/${attr_id}`)

 }
 if(res.meta.status !==200){
    return this.$message.error('删除数据失败！')

 }
 this.$message.sucess('删除数据成功！')
   this.getParamsDate()
  },
  computed:{
  //定义一个计算属性控制按钮需要被禁用，则返回true，否则返回false
   isBtnDisabled(){
   if(this.CateselectKeys.lnegth !==3){
     return true
   }
     return false
   }
   //获取当前选中的分类ID，只要取出数组最后一项就可以了
   cateId(){
    if(this.CateselectKeys.lnegth ===3){
      return this.CateselectKeys[2]
    }
    return null 
   },
   //动态计算标题的文本，根据当前的activeName
   titleText(){
    if(this.activeAame === 'many'){
      return '动态参数'
    }
      return '静态属性'
   },
   文本框失去焦点或者按下了Enter都会触发的函数，展示按钮
   handleInputConfirm(){
row.inputVisible = false
   },
   文本框失去焦点的时候，
   handleInputConfirm(row){
if(row.inputValue.trim().length===0){
  row.inputValue = ''
  row.inputVisible = false
  return
}
如果没有return，则证明输入的内容需要做后续的处理
row.attr_vals.push(row.inputValue.trim())
row.inputValue = ''
row.inputVisible = false
需要发起请求，保存这次接口
this.saveAtteVals()
   点击按钮，展示文本输入框
   $nextTick 方法的作用：当页面上元素被重新渲染之后,才会指定回调函数中的代码。
showInput(row){
   row.inputVisible = true
   this.$nextTick(_ => {
     让文本框自动获得焦点，文本框的DOW对象的焦点
      this.$refs.saveTagInput.$refs.input.focus();
    });
   },
   //删除对应的参数可选项
   handeClose(i,row){
   row.attr_vals.splice(i,1)
   this.saveAtteVals(row)
   },

 async  saveAtteVals(row){
需要发起请求，保存这次接口
const {date:res} = await this.$axios.put(`categories/${this.cateId}/${row.attr_id}`,{
  attr_name:row.attr_name,
  attr_sel:row.activeName,
  attr_vals:row.attr_vals.join(' ')
  })
   },
   }
  },
  create(){  
  this.getCatLsit()
  },
}
</script>
<style lang="less" sopes>
</style>
````
> git branch
> git status
> git add .
> git commit -m '完成了商品分类'
> git push
> git checkout master
> git merge Goods_params


## 商品列表的开发
> git checkout -b Goods_list
> git branch
> git push -u origin goods_list

````
<template>
<!-- 面包屑导航区域 -->
<el-breadcrumb separator="/">
  <el-breadcrumb-item :to="{ path: '/' }">首页</ el-breadcrumb-item>
  <el-breadcrumb-item>商品管理</el-breadcrumb>
  <el-breadcrumb-item>商品列表</el-breadcrumb>
<el-breadcrumb>
<!-- 卡片视图 -->
<el-cart>
   <el-row>
     <el-col :sapn="8">
    <el-input placeholder="请输入内容" 
    v-model="query.queryInfo"
    clearadle 删除属性
    @clear="getGoodsList()" 重新调用删除
    >
    <el-button slot="append" icon="el-icon-search" @click="getGoodsList()"></el-button>
  </el-input>
     </el-col>
      <el-col :sapn="4">
      <el-button type="primary" @click="goaddPage">添加商品</el-button>
      </el-col>
   </el-row>
<!-- 表格 -->
<el-table :data="GoodsList" border stripe>
   <el-table-column type="index"></el-table-column>
   <el-table-column lable="商品名称" prop="goods_name"></el-table-column>
<el-table-column lable="商品价格(元)" prop="goods_price"></el-table-column>
<el-table-column lable="商品重量" prop="goods_weight"></el-table-column>
<el-table-column lable="创建时间" prop="add_time">
   <template slot.spoce ='scope.row'>{{scope.row.add_item|dateFormat}}</template>
</el-table-column>
 <el-table-column>操作
   <template slot.scope="scope">
    <el-button type="primary" size="main" icon="el-icon-edit" @click=""></el-button>
  <el-button type="primary" dsize="main" icon="el-icon-delete" @click="remove(scope.row.goods_id)"></el-button>
</template>
 </el-table-column>
</el-table>
<!-- 分页功能 -->
 <el-pagination
      @size-change="GoodsListSizeChange"
      @current-change="GoodsListCurrentChange"
      :current-page="currentPage4"
      :page-sizes="[10, 15, 20, 25]"
      :page-size="queryInfo.pageSize"
      layout="total, sizes, prev, pager, next, jumper"
      :total="total" background>
    </el-pagination>
</el-cart>
</template>
<script>
export dufault {
  data(){
   return{
     GoodsList:[]
    queryInfo:{
      query:'',
      pageName:1,
      pageSize:20
    },
    total:0,
   }
 },
 //获取商品数据
 created(){
  this.getGoodsList()
 },
 methods:{
 根据分页获取对应的商品列表
 async getGoodsList(){
  const {data:res} = awaitthis.$axios.gte('GoodsList',{params:this.queryInfo})
  if(res.mate.status !== 200){
     return this.$message.error('获取商品列表失败！')
  }
  return this.$message.sucess('获取商品列表成功！')
  this.GoodsList = res.data
  this.total = res.data.total
 },
 //条数
 GoodsListSizeChange(newpageSize){
  this.queryInfo.pageSize = newpageSize
  this.getGoodsList()
 },
 GoodsListCurrentChange(NewpageName){
   this.queryInfo.pageName = NewpageName
   this.getGoodsList()
 },
 //删除数据
async remove(id){
 const confirmResult = await  this.$confirm('此操作将永久删除该商品, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).catch((error)=>{
        })
        if(confirmResult !== 'confirm'){
         return this.$message.info('已经取消删除！')
        }
  const {date:res} await this.$axios.delete('goods/${id}')
  if(res.meat.status !==200){
    return this.$message.error('删除数据失败！')
  }
   this.$message.success('删除数据成功！')
   this.getGoodsList()
 },
 //点击增加跳转到增加商品页面
 goaddPage(){
   this.$router.push('/goods/addpage')
 }
 }
}
 
</script>
<style>


</style>

````
#### 绘制添加商品页面
````
<template>
  <!-- 面包屑导航区域 -->
<el-breadcrumb separator="/">
  <el-breadcrumb-item :to="{ path: '/' }">首页</ el-breadcrumb-item>
  <el-breadcrumb-item>商品管理</el-breadcrumb>
  <el-breadcrumb-item>商品列表</el-breadcrumb>
<el-breadcrumb>
<!-- 卡片视图 -->
<el-cart>
<!-- 提示区域 -->
    <el-alert
    title="警告提示的文案"
    type="info"
    center 
    show-icon :closable = 'false'
    >
<!-- 步骤条 -->
<el-steps :space="200" :active="activeIndex" finish-status="success" align-center>
  <el-step title="基本信息"></el-step>
  <el-step title="商品参数"></el-step>
  <el-step title="商品属性"></el-step>
  <el-step title="商品图片"></el-step>
  <el-step title="商品内容"></el-step>
  <el-step title="完成"></el-step>
</el-steps>
<!-- tab栏区域 -->
<el-form :model="addForm" :rules="addFormrules" ref="addruleForm" label-width="100px" label-position="top" >
  <el-form-item label="活动名称" prop="name">
    <el-input v-model="ruleForm.name"></el-input>
  </el-form-item>
<el-tabs :tab-position="'left'" v-model="activeIndex -0" :before-leave="beforeTabLeave" @tab-click="tabClick">
    <el-tab-pane label="基本信息" name="1">
     <el-form-item label="商品名称" prop="goods_name">
        <el-input v-model="addForm.goods_name"></el-input>
     </el-form-item>
     <el-form-item label="商品价格" prop="goods_price">
    <el-input v-model="addForm.goods_price">
     <!-- 复选框 -->
    <el-checkbox-group v-model="item.attr_vals">
    <el-checkbox :label="cb" v-form="(cb,i) in item.attr_vals"></el-checkbox>
  </el-checkbox-group>
  </el-input>
     </el-form-item>
     <el-form-item label="商品重量" prop="goods_weight">
        <el-input v-model="addForm.goods_weight"></el-input>
     </el-form-item>
     <el-form-item label="商品数量" prop="goods_number">
        <el-input v-model="addForm.goods_number" type="number"></el-input>
     </el-form-item>
   <el-form-item label="商品分类"prop="">
    <el-cascader
    expand-trigger='hove'
    v-model="addForm.goods_cat"
    :options="cartLsit"
    :props="catePoros"
    @change="handleChange">
    </el-cascader>
     </el-form-item>
   </el-tab-pane>
     <el-tab-pane label="商品参数" name="2">
       <el-form-item :label="item.atte_name" v-for="(item.i) in manyTableDate)>{{item}}</el-form-item>
     </el-tab-pane>
    <el-tab-pane label="商品属性" name="2">
     <el-form-item  :lable="item.attr_name" v-for="(item,i) in onlyTabeDate">
     <el-input v-model="item.attr_vals"></el-input>
     </el-form-item>
    </el-tab-pane>
    <el-tab-pane label="商品图片" name="3">
  <!--点击上传图片 -->
  <el-upload
  <!-- action 表示图片要上传到的API接口地址，完整的后地址要完整 
  list-type 处理文件的渲染的UI效果
  -->
  :action="uploadURL" 
  :on-preview="handlePreview"
  :on-remove="handleRemove"
  list-type="picture"
  :headers = "headerObj"
  :on-success="handleSuccess"
  >
  <el-button size="small" type="primary">点击上传</el-button>
</el-upload>
</el-tab-pane>
   <el-tab-pane label="商品内容"  name="4">
      <quill-editor v-model="addForm.goods_introduce"></quill-editor>
      <!-- 添加商品的按钮 -->
    <el-button type="primary" @click="add">添加商品</el-button>
   </el-tab-pane>
  </el-tabs>
  </el-form>
  </el-alert>
</el-cart>
<!-- 显示图片预览的弹框 -->
<el-dialog
  title="提示"
  :visible.sync="prevdialogVisible"
  width="50%"
  >
 <img :src="reviePath">
</el-dialog>
</template>
<script>
 data(){
   return(){
 activeIndex:'0',
 addForm:{
   goods_name:'',
   goods_price:0,
   goods_weight:0,
   goods_number:0,
   goods-cat:[],商品所属的分类数组,
   pice:[],图片上传成功push的数组
   goods_introduce:'',商品详情描述
   attrs:[],
 },
 addFormrules:{
   goods_name:[
       { required: true, message: '请输入商品的名称', trigger: 'blur'
       },
   ],
   goods_price:[
      { required: true, message: '请输入商品的价格', trigger: 'blur'
       }
   ],
   goods_weight:[
      { required: true, message: '请输入商品的重量', trigger: 'blur'
       }
   ],
   goods_number:[
      { required: true, message: '请输入商品的数量', trigger: 'blur'
       },
       goods-cat:[
      { required: true, message: '请选择商品分类', trigger: 'blur'
       },
       ]
   ],
   cateList:[],商品分类
   catePoros:{
     lable:"cat_name",
     value:'cat_id',
     childer:'childer'
   },
   manyTableDate:[] 动态商品
   onlyTabeDate:[] 静态参数
   uploadURL:'http://127.0.0.1:8888/api/private/vl/upload',
   reviePath:''
   prevdialogVisible:false,
   为每一次图片的上传增加ajax请求头对象
   headerObj:{
       Authorization:window.sessionStorage.getItem('token')
   },
   点击富文本的添加
  add(){
   this.$refs.addruleForm.validdate(async(valid)=>{
     if(!valid) {return this.$message.$error('请添加表单')
     }

 深度克隆的包
 lodash cloneDeep(obj)
 const form = _.cloneDeep(this.addForm)
 form.goods_cat = form.goods_cat.join(',')
 处理动态参数
 this.manyTableData.forEach((item)=>{
   const newinfo = {
     attr_id:item.attr_id,
     attr_value:item.attr_vals.join(' ')
   }
   this.addForm.attrs.push(newinfo)
 })
 处理静态属性
   this.onlyTableData.forEach((item)=>{
   const newinfo = {
     attr_id:item.attr_id,
     attr_value:item.attr_vals.join(' ')
   }
   this.addForm.attrs.push(newinfo)
 })
 form.attrs = this.addForm.attrs
 执行添加的行为
 const {data:res} = await this.$axios.post('goods',form)
 if(res.mate !== 200){
   return this.$message.error('商品添加失败!')
 }
  return this.$message.success('商品添加成功！')
  this.$router.push('/goods')
   })
   }
 }
   },
   compted:{
     cateID(){
       if(this.addForm.goods_cat.length ===3){
         return this.addForm.goods_cat[2]
       }
       return null
     },
   }
   methodes:{
    //获取商品分类
   async getCateList(){
   const {data:res} = await this.$axios.get('categories')
   if(res.meta.satus !== 200){
      return this.$message.error('获取商品列表失败！')
   }
      this.cartLsit = res.data
    },
    
    //级联选择器变化会触发的函数
    handleChange(){
     if(this.addForm.goods_cat.length !=== 3){
       this.addForm.goods_cat.length = []
     },

  监听图片上传成功的事件
   handleSuccess(response){
    1、先拼接得到一个图片信息对象
    const picInfo = {pic:response.data.tem_path} 
    this.addForm.pics.push(picInfo)
   },
  处理图片预览效果
     handlePreview(file){
     this.reviePath = file.response.data.url  
     prevdialogVisible = true
     }
     处理移除图片的操作
     handleRemove(file){
      1.获取要删除的临时路劲
      const filePath = file.response.data.tem_path 
      2.从pics数组中找到这个对应的索引
     const i= this.addForm.pics.findIndex((x)=>{
       if(x.pic === filePath)
      })
      3.调用数组splice方法把图签信息对象从pics中移除
      this.addForm.splice(i,1)
     }
    },
    
   监听activeName的切换事件
   activeName即将进入
   oldActiveName即将离开
    beforeTabLeave(activeName,oldActiveName){
      if(oldActiveName === '0' && this.addForm.goods_cat.length !==3){
        this.$message.error('请选择商品分类')
        return false
      }
    },
    监听this.active的函数
  async  tabClick(){
     if(this.activeIndex === '1'){
    const {data:res} = await this.$axios.get(`categories/${this.cateID}`,params{
         sel:'many'
       })
       res.date.forEach((item)=>{
        const item.attr_vals= item.attr_vals.length===0 ? []
        :item.attr_vals.split(' ')
       })
       this.manyTableDate = res.data
     }else{
        if(this.activeIndex === '2'){
        this.$axios.get(`categories/${this.cateID}`,params{
         sel:'only'
       })
       this.onlyTabeDate = res.date
        }
     }
    }
   },
   created(){
    this.getCateList()
   }
 }

</script>
<style></style>
````
> git add .
> git coommit -m '商品' 
> git push
> git checkout master
> git merge goods_list
> git push

## 订单管理开发
> git checkout -b order
> git push -u origin order

````
<template>
 <!-- 面包屑导航区域 -->
<el-breadcrumb separator="/">
 <el-breadcrumb-item :to="{ path: '/' }">首页</      el-breadcrumb-item>
  <el-breadcrumb-item>订单管理</el-breadcrumb>
  <el-breadcrumb-item>订单列表</el-breadcrumb>
<el-breadcrumb>
<!-- 卡片视图 -->
<el-cart>
    <el-row>
      <el-col :sapn="8">
             <el-input placeholder="请输入内容" >
    <el-button slot="append" icon="el-icon-search"></el-button>
  </el-input>
      </el-col>
    </el-row>
    <!-- 订单列表数据 -->
    <el-table :data="derList" border stripe>
      <el-table-cloumn type="index"></el-table-cloumn>
      <el-table-cloumn lable="订单编号" prop="oder_number"></el-table-cloumn>
      <el-table-cloumn lable="订单价格" prop="oder_price"></el-table-cloumn>
      <el-table-cloumn lable="是否付款" prop="pay—satus">
           <template slot-scope="scope">
              <el-tag type="succes" v-if="scope.row.pay.status==='1'">已付款</el-tag>
              <el-tag type="danger" v-else>未付款</el-tag>
         </template>
      </el-table-cloumn>
      <el-table-cloumn lable="是否发货" prop="is_send"></el-table-cloumn>
      <el-table-cloumn lable="下单时间" prop="cater_time">
         <template slot-scope="scope">
             {{scope.row.create_time |dateFormat}}
         </template>
      </el-table-cloumn>
      <el-table-cloumn lable="操作">
         <template slot-scope="scope">
  <el-button type="primary" icon="el-icon-edit" siae="mini" @click="showBox">编辑</el-button>
  <el-button type="success" icon="el-icon-location" siae="mini"@click="shopProgressBox">物流进度的查询</el-button>    
        </template>      
      </el-table-cloumn>
    </el-table>
<!-- 渲染页码 -->
      <el-pagination
      @size-change="derSizeChange"
      @current-change="derCurrentChange"
      :current-page="querzInfo.pagename"
      :page-sizes="[5, 10, 15, 20]"
      :page-size="querzInfo.pagesize"
      layout="total, sizes, prev, pager, next, jumper"
      :total="total">
    </el-pagination>
</el-cart>
<!-- 编辑地址的对话框 -->
<el-dialog
  title = "修改地址"
  :visible.sync="addDialogVisible"
  width="50%"
  @close="addresDialogClosed"
  >
    <el-form :model="addruleForm" :rules="addrules" ref="addruleForm" label-width="100px" class="demo-ruleForm">
  <el-form-item label="省市区/县" prop="addressl">
    <el-input v-model="addruleForm.address1">
        <!-- 级联选择器 -->
        <el-cascader :options="cityData" v-model="addruleForm.address1"></el-cascader>
    </el-input>
  </el-form-item>
   <el-form-item label="详细地址" prop="address2">
    <el-input v-model="addruleForm.address2"></el-input>
  </el-form-item>
  </el-form>
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </span>
</el-dialog>

<!-- 物流进度地址对话框 -->
<el-dialog
  title="物流进度"
  :visible.sync="progresVisible"
  width="50%"
  >
  <!-- 物流时间线 -->
  <el-timelin >
    <el-timeline-item
      v-for="(activity, index) in progressinfo"
      :key="index"
      :time="activity.timep">
      {{activity.context}}
    </el-timeline-item>
  </el-timeline>
</el-dialog>
</template>
<script>
 export dufalu {
   data(){
     return{
      querzInfo:{
        query:'',
        pagename:1,
        pagesize:10,
      }
      total:0,
      derList:[], 
      addDialogVisible= false,
      addruleForm:{
       address1:[],
       address2:'',
      },
      addrules:{
        address1:[
         { required: true, message: '请输入省市区/县', trigger: 'blur' },

        ],
        address2:[
           { required: true, message: '请输入详细地址', trigger: 'blur' },
        ]
      },
progresVis:false,
progressinfo:[],

   },
   methods:{
async getOrderList(){
const {data:res} = await this.$axios.get('oders',params:{this.querzInfo}
if(res.mate.status !== 200){
  return this.$message.error('获取订单列表失败!')
}
  this.derList = res.data
  this.total = res.data.total
},
//页数
derCurrentChange(newpagename){
  this.querzInfo.pagename = newpagename
   this.getOrderList()
}
//条数
derSizeChange(newpageSize){
this.querzInfo.pagesize = newpageSize
 this.getOrderList()
}
//展示编辑地址到对话框
showBox(){
addDialogVisible = true
},
addresDialogClosed(){
  this.$refs.addruleForm.resetFields()
},
//物流进度查询
async shopProgressBox(){
const {data:res} = await this.$axios.get('/kuaidi/:id/804909574412444580')
if(res.meta.status !== 200){
   return this.$message.error('获取物流信息失败！')
}
this.progressinfo = res.date
this.progresVisible = true
}
this
   },
   created(){
   this.getOrderList()
   },
 }
</script>
````
> git add .
> git commit -m '订单管理'
> git push
> git checkout master
> git meage order
> git push

## 数据报表的开发
npm install echarts --save 下载

> git checkout -b report 
> git push -u origin report

````
 <template>
<!-- 面包屑导航区域 -->
<el-breadcrumb separator="/">
 <el-breadcrumb-item :to="{ path: '/' }">首页</      el-breadcrumb-item>
  <el-breadcrumb-item>数据统计</el-breadcrumb>
  <el-breadcrumb-item>数据报表</el-breadcrumb>
<el-breadcrumb>
<!-- 卡片视图 -->
<el-cart>
<!-- 2.为ECharts准备一个具备大小（宽高）的Dom -->
<div id="main" style="width: 600px;height:400px;"></div>
</el-cart>
 </template>
  <script>
  1.导入 echarts
  import echarts from 'echarts'

  import _ form 'lodash'
  export default {
    data(){
      return{
        //需要合并的数据
        option :{
            title: {
                text: 'ECharts 入门示例'
            },
            tooltip: {},
            legend: {
                data:['销量']
            },
            xAxis: {
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }]
        };
      }
    },
    methods:{
3.基于页面上的元素，已经被渲染完了
var myChart = echarts.init(document.getElementById('main'));

获取要渲染的图像数据
const {data:res} = this.$axios.get('repotrs/type/1')
if(res.meta.status !== 200){
   return this.$message.error('获取数据失败！')
}
4.准备数据和配置资源,把服务器返回的数据对象和data里的option合并成一个新的对象！merge==> lodash提供的
const result = _.merge(res.data,this.options)
  5.展示数据
  myChart.setOption(result)
    },
    mounted:{
    }
    created(){
    }
  }
  </script>
  <style>
  
  </style>
````
> git add .
> git commit -m '商品图表'
> git push
> git checkout master
> git merge report
> git push
> git reset --mixed 代码回滚，提交错的代码回滚到工作区
> git reset --hard 代码回滚，提交错的代码回滚到缓存区
> git reset --soft 代码回到版本区
> git log 提交的操作
> git revert       

## 给自己的项目加上一个进度条第三方
1.npm install --save nprogress
2.在拦截器里调用请求拦截之前调用NProgress.start();
3.在数据请求回来之后，响应之后隐藏进度条NProgress.done();
````
import NProgress from 'nprogress'
import 'nprogress/nprogress.css'

在request 拦截器中,展示进度条NProgress.start()
axios.interceptors.request.use((config)=>{
  config.headers.Authourization = window.sessionsStorage.getItem('token')
  NProgress.start()
  return config
})

在response拦截器中展示进度条NProgress.done()
axios.interceptors.response.use((config)=>{
  NProgress.done()
  return config
})
````
##### 项目开发完后优上线
# 项目优化策略
  **在生产环境
  解决serve命令中提示的ESLint语法错误
  运行build命令期间移除所有的console 在build阶段
  https://www.npmjs.com/package/babel-plugin-transform-remove-console
  npm install babel-plugin-transform-remove-console --save-dev
  1.在.bable  "plugins": ["transform-remove-console"]
  2.或者bable.config.js "plugins": ["transform-remove-console"]
会出现的问题：因为bable.config.js "plugins"不管是开发阶段还是生产阶段都会执行的。所以在执行之前判断一下
```
able.config.js{
  const prodplugins = []
  //判断是不是在发布模式，如果是就push，不是就是开发环境
  if(process.env.NOOE_EVN === 'production'){
    prodplugins.push('transform-remove-console')
  }
  //发布产品时候的插件
  ...prodplugins
}

```

## 1.生成打包报告
  vue-cli-service-build --report

## 2.第三方启用CDN
## 3.Element-UI 组件按需加载
## 4.路由懒加载
下载插件 
bable.config.js 配置

## 5.首页内容制动


注册一个全局的过滤器
Vue.filter('dateFormat',function(originVal){
  const dt = new Date(originVal)
  const y = dt.getFulYear()
  const m = (dt.getMount() +1+'').padStart(1,'0')
  const d = (dt.getDate()+ '').padStart(2,'0')
  const hh = (dt.getHours()+'').padStart(2,'0')
  const mm = (dt.getMinutes()+'').padStart(2,'0')
  const ss = (dt.getSeconds()+'').padStart(2,'0')
  return `${y}-${m}-${d} ${hh}:${mm}:${ss}`
})


###  vant的学习 https://youzan.github.io/vant/#/zh-CN/
vant 在真实项目中的用法：下载好以后有两种方式
1.导入全部组件 在mai.js里  import Vant from 'vant' Vue.use(Vant) 在引入css
 <vant-icon name="like-o"></vant-icon> 直接在组件里用

2.按需导入组件,注意在组件里按需导入的时候可以一直.use
 npm i babel-plugin-import -D
 使用babel-plugin-import插件实现按导入
 在main.js里
 import {Button,DropdownMenu} from 'vant' Vue.use(Button).use(DropdownMenu)

 温馨提示：如果使用了按需导入，也就是在.babel的plugins中配置了。需要在改回全局导入的时候注释掉即可。


面试题：
为什么vue组件中的里的data 不是一个对象而是一个函数？
1.如果两个实例引用同一个对象，当一个实例属性发生改变时，另一个实例也会随之改变
  只有两个实例有自己的作用域时，才不会互相干扰。
2.这是因为就JavaScript的特性所致，在compontent中，data必须以函数的形式存在，不可以是对象。
总结：组件中的data写成一个函数，数据以函数返回值的形式定义，这样复用组件的时候，都会返回一个新的data，
     自己的作用域数据不会相互干扰


### Vant + Vue仿照Boos直聘
1.下载vant后按需引入，直接安装按需引入
2.在项目根目录下找到.babelrc


## 准备面试题
1.css中的盒子模型有

## 箭头函数小结
箭头函数没有prototype(原型)，所以箭头函数本身没有this
箭头函数的this在定义的时候继承自外层第一个普通函数的this。
如果箭头函数外层没有普通函数，严格模式和非严格模式下它的this都会指向window(全局对象)
箭头函数本身的this指向不能改变，但可以修改它要继承的对象的this。
箭头函数的this指向全局，使用arguments会报未声明的错误。
箭头函数的this指向普通函数时,它的argumens继承于该普通函数
使用new调用箭头函数会报错，因为箭头函数没有constructor
箭头函数不支持new.target
箭头函数不支持重命名函数参数,普通函数的函数参数支持重命名
箭头函数相对于普通函数语法更简洁优雅
箭头函数不能当做Generator函数,不能使用yield关键字(python)



###  css 中会遇到的问题

## css 选择器的优先级

## H5和CSS3之间的区别
....
 text-align:文本对齐方式
 text-decoraiton:s首行缩进
 想让元素在一行显示
 display:inline-block  
 让块元素在一行显示
 内联支持宽高
 默认内容撑开宽度
 标签之间换行被解析

 ## 浮动 
 让块元素在一行显示
 内联支持宽高
 默认内容撑开宽度
 脱离文档流
 提升层级关系
 1. 使元素脱离文档流，按照指定的方向发生移动，
    遇到父级或者相邻的浮动元素会停下来
    
 flocta:left/right/none/inherit;

 ## 清除浮动
 清除浮动带来的影响
 1.给浮动元素的父级加增加高度。（能解决问题但是扩展性不好，万一父元素的高度拿不到呢？）
 2.overflow: hidden;
 3.clear:after{
    content:"",
    display:block;
    clear:both;
 } // 不考虑兼容的情况下 如果要考虑 .clear{*zomm:1} IE6/IE7
 clear:both 左右两边都不能有浮动 

## 什么是BFC BFC是块级格式上下文，是用来做盒子的横向布局的
0. 浏览器中创建了一个独立的渲染区域，该区域的所有元素的布局不会
   影响到区域外面的元素布局，只对块级元素起作用。
1. 比如说一个大盒子里有两个盒子想让他们在同一行显示很简单
   display:inline-block 就行了，但是盒子是在一行显示了
   但是两个盒子之间有间隙，那是因为内联块盒子代码解析出来的是空格换行出来的
   解决的办法就是父级的盒子加一个font-size: 0，但是加了后如果
   父盒子里有文字，那文字就显示不出来
....

## 预览图片
![龙hiahia](图地址)

## 超链接
[妙味](https://baike.baidu.com)

## 代码块
```JavaScript
var a = 12
```
## 表格
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |

## vue里引人虚拟DOM是为了解决什么问题？
1. 获取监听变化后生成的虚拟节点树
2. 与上一次虚拟DOM节点树进行比较
3. 找到差异的部分，渲染到真实的DOM节点上面
4. 更新试图

## Vue里数据传递的方法和实例 局部组价的打油诗： 声子 挂子 用子
 import Vue form vue 共公的实例 
1. vue.prototype.$bus = EventBus 挂载到Vue的原型上
   $on事件 $emit触发  
```javascript
//底部绑定购物车的点击事件把值App.vue的值传过去
this.$bus.$on('pinkName',(data)=>{
 this.pinkName += data
})

//触发$bus事件绑定的函数，点击加入购物车的时候把数值传过去给App的pinkName
this.$bus.$emit("sendPickNaum",this.pinkName)
```
2. props属性传值 $emit事件  
   + 父传子 1.parent 2.chiled
```javascript 
// 父
Vue.component('Parent',{
     data(){
       return{
         msg:"我是父组件！"
       }
     },
     template:
     `
     <div>
     <Child/>
     </div>
     `
     


}),
//子组件
Vue.component('Child',{
     data(){
       return{
         text:"我是子组件！"
       }
     },
     template:
    `
    <div>
     <input type="text" v-model="msg"/>
    
    </div>
    `
     


})



let vm = new Vue({
  el:'#app',
  data(){
    return{
      msg:'实例'

    }
  },
  components:{

  },
  template:
  `
  <div id="app">
  <Patent/>
  </div>
  `
})
```

### 点击返回 && 监听路由如果是首页就把返回隐藏
````javascript
<span @click= "goBack" v-show="flag">返回</span>
 data(){
   return{
    flag:false
   }
 },
 methods:{
  goBack(){
    this.$outer.go(-1)
  }
 },
 watch(){
   "$router.path"(newVla){
     if(newVla==='/home'){
       this.flag = false
     }else{
       this.flag = true
     }

   }
 }

***** 会遇到的问题，因为在个别组件里还是会有检测不到路由的改变，导致search组件里的头部的返回按钮还在,组件没有跟新完检测不到路由解决的办法就是在 created钩子函数里在做一次处理 

created(){
  this.flag = $router.path ==='/home' ? true : false;
}
````
 


## 视口分为布局视口 和 理想视口
 + meta 视口标签
## 移动端开发选择（移动端主流方案）
 1. 单独制作移动端页面(主流)
  - 京东https://m.jd.com/  网易严选 http://m.you.163.com/
  - 通常情况下，网址域名前加m(mobeile)的可以打开移动端。
    通过判断设备的不同，如果是移动端设备，则跳转到移动端页面。
  - 在网页拿图 open in new tab
 2. 响应式页面兼容移动端（其次）
  - 三星就写一个页面
  - 响应式布局是通过屏幕的宽度来改变样式，以适应不同终端。
  问题：要解决很多HTML5 和 CSS3 带来的兼容问题。
  header-footer-nav-main-

  ## 移动端的常见问题解决方案
   1. 移动端浏览器
    - 移动端浏览器大多以webkit内核为主，因此需要考虑webkit的兼容问题。
    - 我们可以放心使用H5标签和CSS3样式。
    - 同时我们浏览器的私有前缀我们只需要加-webkit-即可。
   2. 移动端样式初始化
    - 移动端的初始化样式，推荐使用normalize.css
   3. css3 有了自己新的盒子模型 
    - box-sizing：content-box 传统的盒子模型
    - box-sizing：border-box (从边框开始算)
    - 有了这句话就让盒子模型变成css3,保持盒子原有的宽。
      padding和border，不会在撑大盒子了
   4. 特殊样式
    - a标签自带的点击高亮我们需要清除，用transparent
    - webkit-tap-highlight-color:transparent;
    - 清除在移动端iOS，按钮上自带的样式
    - -webkit-appearance:none;
    - 禁止长按页面时提出菜单
    - img,a{-webkit-touch-callout:none}
[css初始化](http://necolas.github.io/normalize.css/)

温馨提示:在布局过程中因为图片是行内块所以图片 
        所以想让图片居中要加vertical-align:middle

##  移动端rem 布局完美解决方案
    ****rem 适配布局
  1. 页面布局文字是否能随着屏幕的大小而变化。
  2. 百分比布局和flex布局都是针对宽度布局的，那高度呢？
  3. 怎样让屏幕发生变化的时候元素高度和宽度都等比例缩放？

## 媒体查询 ？？？
  1. 媒体查询是什么？ (Media Query) 是css3新语法！
  2. 使用@Media查询，可以针不同的类型定义不同的样式！
  3. 当重置浏览器的大小过程中国，页面也会根据浏览器的高度和宽度重新渲染页面！

```css 视口就是浏览器显示页面的屏幕区域

@media screen and (max-widthz:320px){
       

}

 
```
## rem 适配
github: https://github.com/amfe/lib-flexible

## Ps 应用   
443812682@qq.com 1761159159
在线代码格式化 （翻译别人的代码）