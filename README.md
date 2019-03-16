# 笔试题  

请完成以下笔试题，可以使用自己擅长的语言来编写，通过 github pull request 提交代码。

1. 编写一个递归版本的 reverse(s) 函数(或方法),以将字符串s倒置。
	function reverse(s){
                 if(s.length<=1){
					 return s;
				 } else{
					 return reverse(s.substr(1))+s.charAt(0);
				 }

              }
			  var s=reverse("abcde");
			  console.log(s);

2. 编写程序 expr，以计算从命令行输入的逆波兰表达式的值，其中每个运算符或操作数用一个单独的参数表示。例如，命令
expr 2 3 4 + *

3. 用归并排序将3，1，4，1，5，9，2，6 排序。
 function mergeArray(arr, first, mid, last, temp) {
                              var i=first;
                              var m=mid;
                              var j=mid+1;
                              var n=last;
                              var k=0;
                          while(i<=m && j<=n) {
                              if(arr[i] < arr[j]) {
                                    temp[k++] = arr[i++];
                              } else {
                                    temp[k++] = arr[j++];
                                     }
                                               }
                          while(i<=m) {
                                    temp[k++] = arr[i++];
                                      }
                          while(j<=n) {
                                    temp[k++] = arr[j++];
                                      }  
                          for(let l=0; l<k; l++) { 
                                    arr[first+l] = temp[l];
                                                }
                                     return arr;
                                 }
              // 递归实现归并排序
            function mergeSort(arr, first, last, temp) {
                   if(first<last) {
                            var mid = Math.floor((first+last)/2);
                                 mergeSort(arr, first, mid, temp);    // 左子数组有序
                                 mergeSort(arr, mid+1, last, temp);   // 右子数组有序
                                 arr = mergeArray(arr, first, mid, last, temp);  
                                 }
                              return arr;
                            }
			           var a=[3,1,4,1,5,9,2,6];
			            var b=[];
			           var s=mergeSort(a,0,a.length-1,b);
			              console.log(s);

4. 对下面的 json 字符串 serial 相同的进行去重。

```javascript
  [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];
```
var arr= [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];
  var json=JSON.stringify(arr);
  function myfun(json){
	  var arr=JSON.parse(json);
	  for(var i=0;i<arr.length;i++){
		  for(var j=i+1;j<arr.length;j++)
		  if(arr[i].serial===arr[j].serial){
			  arr.splice(j,1);
			  j--
		  }
	  }
	  return arr;
  }
  var a=myfun(json);
  json=JSON.stringify(a);
  console.log(json);

5. 把下面给出的扁平化json数据用递归的方式改写成组织树的形式

```javascript
  [
    {
      "id": "1",
      "name": "中国",
      "code": "110",
      "parent": ""
    },
    {
      "id": "2",
      "name": "北京市",
      "code": "110000",
      "parent": "110"
    },
    {
      "id": "3",
      "name": "河北省",
      "code": "130000",
      "parent": "110"
    },
    {
      "id": "4",
      "name": "四川省",
      "code": "510000",
      "parent": "110"
    },
    {
      "id": "5",
      "name": "石家庄市",
      "code": "130001",
      "parent": "130000"
    },
    {
      "id": "6",
      "name": "唐山市",
      "code": "130002",
      "parent": "130000"
    },
    {
      "id": "7",
      "name": "邢台市",
      "code": "130003",
      "parent": "130000"
    },
    {
      "id": "8",
      "name": "成都市",
      "code": "510001",
      "parent": "510000"
    },
    {
      "id": "9",
      "name": "简阳市",
      "code": "510002",
      "parent": "510000"
    },
    {
      "id": "10",
      "name": "武侯区",
      "code": "51000101",
      "parent": "510001"
    },
    {
      "id": "11",
      "name": "金牛区",
      "code": "51000102",
      "parent": "510001"
    }
  ];
```
var arr= [
    {
      "id": "1",
      "name": "中国",
      "code": "110",
      "parent": ""
    },
    {
      "id": "2",
      "name": "北京市",
      "code": "110000",
      "parent": "110"
    },
    {
      "id": "3",
      "name": "河北省",
      "code": "130000",
      "parent": "110"
    },
    {
      "id": "4",
      "name": "四川省",
      "code": "510000",
      "parent": "110"
    },
    {
      "id": "5",
      "name": "石家庄市",
      "code": "130001",
      "parent": "130000"
    },
    {
      "id": "6",
      "name": "唐山市",
      "code": "130002",
      "parent": "130000"
    },
    {
      "id": "7",
      "name": "邢台市",
      "code": "130003",
      "parent": "130000"
    },
    {
      "id": "8",
      "name": "成都市",
      "code": "510001",
      "parent": "510000"
    },
    {
      "id": "9",
      "name": "简阳市",
      "code": "510002",
      "parent": "510000"
    },
    {
      "id": "10",
      "name": "武侯区",
      "code": "51000101",
      "parent": "510001"
    },
    {
      "id": "11",
      "name": "金牛区",
      "code": "51000102",
      "parent": "510001"
    }
  ];
  var json=JSON.stringify(arr);
  arr=JSON.parse(json);
  console.log(arr);
  function myfun(data,parent){
	  var result=[];
	  var temp;
	  for(var i=0;i<data.length;i++){
		  if(data[i].parent==parent){
			  var obj=data[i];
			  temp=myfun(data,data[i].code);
			  if(temp.length>0){
				  obj.children=temp;
			  }
			  result.push(obj);
		  }
		  
	  }
	  return result;
  };
console.log(myfun(arr,""));