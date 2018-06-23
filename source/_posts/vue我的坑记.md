---
title: vue我的坑记
date: 2018-06-07 21:42:30
tags: vue
---

#### element UI select下拉选项位置问题

在使用elementUI下拉选项时，可能存在下拉时下拉列表选项框的位置距离下拉框所在的位置距离过大，这个是由于elementUI自己设置的根据下拉框位置定位，而他可能是根据position:absolute;来进行定位的,而我们要在全局设置他的 position:fixed !important;即可。(注意使用!important增加权重)


<!-- more -->

附加position各种值

* absolute:生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
* fixed:生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
* relative:生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。
* static:默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。
* inherit:规定应该从父元素继承 position 属性的值。


#### element UI 组件默认传参和自定义传参的解决方法

如下代码
```

        <div v-for="(item,index) in object.cooperationDepartmentNumber">
          <div class="entrustingPartyList">
            <el-row>
              <el-col :span="12"> 
                <el-form-item label="协办单位">
                <el-autocomplete
                  class="inline-input"
                  v-model="object.cooperationDepartment.otherArray[index].unit"
                  :fetch-suggestions="unitQuerySearch"
                  placeholder="请输入协办单位"
                  :trigger-on-focus="false"
                  @select="unitHandleSelect"
                ></el-autocomplete>
                </el-form-item>
              </el-col>
              <el-col :span="12"> 
                <el-form-item label="协办部门" v-show="interior">
                  <el-input v-model="object.cooperationDepartment.otherArray[index].cooperation" placeholder="协办部门"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="12"> 
                <el-form-item label="协办单位联系人" v-show="external">
                  <el-input v-model="object.cooperationDepartment.otherArray[index].cooperation" placeholder="协办部门"></el-input>
                </el-form-item>
              </el-col>
            </el-row>
          </div>
        </div>

```

当我们v-for有很多个相同的组件时，我们需要知道选中的是第几个组件,那么我们肯定想要知道对应的[index],你会想到下面这样[item]是默认的值
```

	  <el-col :span="12"> 
	    <el-form-item label="协办单位">
	    <el-autocomplete
	      class="inline-input"
	      v-model="object.cooperationDepartment.otherArray[index].unit"
	      :fetch-suggestions="unitQuerySearch"
	      placeholder="请输入协办单位"
	      :trigger-on-focus="false"
	      @select="unitHandleSelect(item, index)"
	    ></el-autocomplete>
	    </el-form-item>
	  </el-col>
```
解决办法是写个闭包，这样index就表示你的第几个组件
```

	  <el-col :span="12"> 
	    <el-form-item label="协办单位">
	    <el-autocomplete
	      class="inline-input"
	      v-model="object.cooperationDepartment.otherArray[index].unit"
	      :fetch-suggestions="unitQuerySearch"
	      placeholder="请输入协办单位"
	      :trigger-on-focus="false"
	      @select="((item)=>{unitHandleSelect(item, index)})"
	    ></el-autocomplete>
	    </el-form-item>
	  </el-col>
```
这样你在调用这个方法的时候就可以知道是第几个组件对应的了，然后就可以对那个组件进行操作了。


#### vue路由跳转参数传递


发送方路由跳转方法时
```

	  clickRowValFun(data){
        this.$router.push({path:'/pending-particulars/'+data.id});
      },
```
在需要跳转的路由后面加上你需要传递的参数

设置路由时
```

	     {
          path: '/pending-particulars/:projectId',
          name: 'pendingParticulars',
          component: PendingParticulars
        },
```

接收方接收时
```

 	created(){
      this.projectId = this.$route.params.projectId;
    }
```