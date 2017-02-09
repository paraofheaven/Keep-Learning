## �������DOM

Ŀ¼��
- 1 ǰ��
- 2 ǰ��Ӧ��״̬����˼��
- 3 Virtual DOM �㷨
- 4 �㷨ʵ��
	- 4.1 ��js����ģ��Dom��(render)
	- 4.2 �Ƚ���������Dom���Ĳ���(diff)
	- 4.3 �Ѳ���Ӧ�õ�������Dom����(patch)

- 5 С��

## 1 ǰ��

������Ҫ�������ʱ���ڶ�reactʵ����ѧϰ���ܽ�֮һ��react��virtual domһֱ��react�������������ɫ��ϣ���ڱ�ƪ����֮���ҿ��Զ�virtual dom�и������⡣����������⻹ͣ����Ƥë�׶Ρ�
������ʵ�ֵ��������뽫�ῼ�Ǵ����[�ҵ�Github]()��

## 2 ��ǰ��Ӧ��״̬�Ĺ���˵��ȥ

![react png](https://camo.githubusercontent.com/ac106f4ec3a61bb86f6e94d5f6dda8da668e5415/687474703a2f2f6c69766f7261732e6769746875622e696f2f626c6f672f7669727475616c2d646f6d2f736f72742d7461626c652e706e67) 

��������ı�񲼾֣������úü��ֲ�ͬ�ķ�ʽ��ʵ�֡������׵�Ҳ����ǳ�Եľ�����Ҫ��js������洢���������ݣ�

```
	var sortKey = "new" //������ֶΣ�����(new),ȡ��(cancel),��ע(gain),�ۻ�(cumulate)
	var sortType = 1 //�������flag
	var data=[{...}{...}{...}]  //��Ӧ���ݽṹ
```

�������ֶηֱ�洢��ǰ������ֶΡ������򡢻��б�����ݣ�Ȼ������ͷ���ӵ���¼������û�����ض����ֶε�ʱ�򣬸������漸���ֶδ洢�������������ݽ�������Ȼ���� JS ���� jQuery ���� DOM������ҳ�������״̬����ͷ���Ǽ�����ͷ��ʾ��ǰ����״̬��Ҳ��Ҫ���£��ͱ�����ݡ�

�������ᵼ�µĺ�����ǣ�����Ӧ�ó���Խ��Խ���ӣ���Ҫ��JS����ά�����ֶ�ҲԽ��Խ�࣬��Ҫ�����¼������¼��ص��ø���ҳ���DOM����ҲԽ��Խ�࣬Ӧ�ó�����÷ǳ���ά������������ʹ���� MVC��MVP �ļܹ�ģʽ��ϣ���ܴӴ�����֯��ʽ������ά�����ָ���Ӧ�ó�����Ѷȡ����� MVC �ܹ�û�취��������ά����״̬��Ҳû�н���״̬��������Ҫ��ҳ��ĸ��²�����ǰ����˵����DOM������������Ҫ������DOM������Ҫ������ֻ�ǻ��˸��ط���

��Ȼ״̬�ı���Ҫ������Ӧ��DOMԪ�أ�Ϊʲô����һ��������������ͼ��״̬���а󶨣�״̬�������ͼ�Զ�������Ͳ����ֶ�����ҳ���ˡ�����Ǻ������������ MVVM ģʽ��ֻҪ��ģ����������ͼ����Ǻ�ʲô״̬���а󶨵ģ�˫�������ͻ���״̬���µ�ʱ���Զ�������ͼ��

MVVM ���ԺܺõĽ�������ά��״̬ -> ��ͼ�ĸ��ӳ̶ȣ������ٴ����е���ͼ�����߼�����
�����ⲻ��Ψһ�İ취������һ���ǳ�ֱ�۵ķ��������Դ�󽵵���ͼ���µĲ�����һ��״̬�����˱仯������ģ������������Ⱦ������ͼ��Ȼ�����µ���ͼ�������ɵ���ͼ����������ı�񣬵��û������ʱ�򣬻�����JS�������״̬������ҳ����¾Ͳ����ֶ����� DOM �ˣ�ֱ�Ӱ����������ģ������������Ⱦһ�飬Ȼ������һ��innerHTML�������ˡ�

��������������������ḻ����һ����һʱ����ʶ�����������ᵼ�ºܶ�����⡣��������������������������Ϊ��ʹһ��СС��״̬�����Ҫ���¹������� DOM���Լ۱�̫�ͣ������������Ļ���input��textarea�Ļ�ʧȥԭ�еĽ��㡣���Ľ��ۻ��ǣ����ھֲ���С��ͼ�ĸ��£�û�����⣨Backbone������ô�ɵģ������Ƕ��ڴ�����ͼ����ȫ��Ӧ��״̬�����ʱ����Ҫ����ҳ��϶�ֲ���ͼ��ʱ����������������ȡ��

*��������Ҫ���׺ͼ�ס��������*����Ϊ������ᷢ�֣�*��ʵ Virtual DOM ������ô���ģ�ֻ�Ǽ���һЩ�ر�Ĳ��������������� DOM �����*��

����һ����Ҫע��ľ��ǣ������ṩ�ļ��ַ�������ʵ���ڽ��ͬһ�����⣺ά��״̬��������ͼ����һ���Ӧ�õ��У�����ܹ��ܺ÷�����Ӧ��������⣬��ô�ͼ��������˴󲿷ָ����ԡ�

## 3 Virtual DOM�㷨

DOM�Ǻ����ģ�׼ȷ����˵��DOM��CRUD�����Ǻܺ����ܵġ���ͼ��һ���򵥵�divԪ�ص����ԡ�
~[](https://camo.githubusercontent.com/99c6493c947b4b543e47cca917303af5c876a7f8/687474703a2f2f6c69766f7261732e6769746875622e696f2f626c6f672f7669727475616c2d646f6d2f646f6d2d617474726962757465732e706e67)

��������ǵ�һ�㡣������ DOM Ԫ�طǳ��Ӵ�������Ϊ��׼������ô��Ƶġ����Ҳ������ǵ�ʱ����ҪС��������΢�Ĵ������ܾͻᵼ��ҳ�����ţ������ɱ�����ܵ�������ס�

����� DOM ����ԭ���� JavaScript �������������죬���Ҹ��򵥡�DOM ���ϵĽṹ��������Ϣ���Ƕ����Ժ����׵��� JavaScript �����ʾ������

```
	var element ={
		tagName:'ul',  //�ڵ��ǩ��
		props:{        //DOM�����ԣ��洢��ֵ��
			id:'list'
		},
		children:[     //�ӽڵ�����
			{tagName:'li',props:{class:'item'},children:["Item 1"]},
			{tagName:'li',props:{class:'item'},children:["Item 2"]},
			{tagName:'li',props:{class:'item'},children:["Item 3"]}
		]
	}
```

�����Ӧ��HTML�ṹ�ǣ�

```
	<ul id='list'>
		<li class="item">Item 1</li>
		<li class="item">Item 2</li>
		<li class="item">Item 3</li>
	</ul>
```

��Ȼԭ�� DOM ������Ϣ�������� JavaScript ��������ʾ������������Ϳ��Ը�������� JavaScript �����ʾ�����ṹ������һ��������DOM����

֮ǰ���½���˵�ģ�״̬���->������Ⱦ������ͼ�ķ�ʽ������΢�޸�һ�£��� JavaScript �����ʾ DOM ��Ϣ�ͽṹ����״̬�����ʱ��������Ⱦ��� JavaScript �Ķ���ṹ����Ȼ��������ʵûʲô���ã���Ϊ������ҳ����ʵû�иı䡣

���ǿ���������Ⱦ�Ķ�����ȥ�;ɵ������жԱȣ���¼�����������졣��¼�����Ĳ�ͬ����������Ҫ��ҳ�������� DOM ������Ȼ�������Ӧ���������� DOM ���ϣ�ҳ��ͱ���ˡ������Ϳ�����������ͼ�Ľṹȷʵ������ȫ����Ⱦ�ˣ�����������DOM��ʱ��ȷʵֻ����в�ͬ�ĵط���

�������ν�� Virtual DOM �㷨����Ӧ������������裺

1. �� JavaScript ����ṹ��ʾ DOM ���Ľṹ��Ȼ�������������һ�������� DOM �����嵽�ĵ�����
2. ��״̬�����ʱ�����¹���һ���µĶ�������Ȼ�����µ����;ɵ������бȽϣ���¼����������
3. ��2����¼�Ĳ���Ӧ�õ�����1��������������DOM���ϣ���ͼ�͸�����

Virtual DOM �����Ͼ����� JS �� DOM ֮������һ�����档

## 4 �㷨ʵ��

### 4.1 ����һ����js����ģ��DOM��

�� JavaScript ����ʾһ�� DOM �ڵ��Ǻܼ򵥵����飬��ֻ��Ҫ��¼���Ľڵ����͡����ԣ������ӽڵ㣺

element.js

```
	function Element(tagName,props,children){
		this.tagName = tagName;
		this.props =props;
		this.children=children;
	}
	
	module.exports = function(){
		return new Element(tagName,props,children)
	}
```

��������DOM�ṹ�Ϳ��Լ򵥵ı�ʾΪ��

```
	import el from('./element');
	
	var ul =el('ul',{id:'list'},[
		el('li',{class:'item',['Item 1']}),
		el('li',{class:'item',['Item 2']}),
		el('li',{class:'item',['Item 3']})
	])
```

����ulֻ��һ�� JavaScript �����ʾ�� DOM �ṹ��ҳ���ϲ�û������ṹ�����ǿ��Ը������ul����������<ul>��

```
	Element.prototype.render =function(){
		var el =document.createElement(this.tagName);
		var props =this.props;
		
		for(var propName in props){
			var propValue =props[propName];
			el.setAttribute(propName,propValue)
		}
		var children =this.children || [];
		
		children.forEach(function(child){
			var childEl=(child instanceof Element) ?
				child.render() // ����ӽڵ�Ҳ������DOM���ݹ鹹��DOM�ڵ�
				:document.createTextNode(child)
			el.appendChild(childEl)
		})
		return el;
	}
```

render���������tagName����һ��������DOM�ڵ㣬Ȼ����������ڵ�����ԣ����ݹ�ذ��Լ����ӽڵ�Ҳ�����������������ɵ�Dom�ڵ���ӵ�body�С�

```
	var urlRoot =ul.render();
	document.body.appendChild(urlRoot);
```

### 4.2 ��������Ƚ�����virtual dom���Ĳ���
�ⲿ�ֵ������������ڵ�ˮƽ��⻹�Ƚϱ�������Ҫ�Ժ��ѧϰ���ơ������ȼ򵥽�һ����
��������Ԥ�ϵģ��Ƚ�����DOM���Ĳ����� Virtual DOM �㷨����ĵĲ��֣���Ҳ����ν�� Virtual DOM �� diff �㷨������������ȫ�� diff �㷨��һ��ʱ�临�Ӷ�Ϊ O(n^3) �����⡣������ǰ�˵��У�����ٻ��Խ�㼶���ƶ�DOMԪ�ء����� Virtual DOM ֻ���ͬһ���㼶��Ԫ�ؽ��жԱȣ�

![](https://camo.githubusercontent.com/a32766a14f6b7fbe631475ed1a186fbd9de7f2c3/687474703a2f2f6c69766f7261732e6769746875622e696f2f626c6f672f7669727475616c2d646f6d2f636f6d706172652d696e2d6c6576656c2e706e67)

�����divֻ���ͬһ�㼶��div�Աȣ��ڶ��㼶��ֻ����ڶ��㼶�Աȡ������㷨���ӶȾͿ��Դﵽ O(n)��

#### 4.2.1 ������ȱ�������¼����

��ʵ�ʵĴ����У�����¾�����������һ��������ȵı�����������ÿ���ڵ�һ��Ψһ�ı�ǡ�

![](https://camo.githubusercontent.com/6cdc35026bcbb6aa0f8fb4aaca3596963192a7f3/687474703a2f2f6c69766f7261732e6769746875622e696f2f626c6f672f7669727475616c2d646f6d2f6466732d77616c6b2e706e67)

��������ȱ�����ʱ��ÿ������һ���ڵ�ͰѸýڵ���µĵ������жԱȡ�����в���Ļ��ͼ�¼��һ���������档

```
	funciton diff(oldTree,newTree){
		var index = 0; //��ǰ�ڵ�ı��
		var patches={}  //����ÿ���ڵ�������ʱ����
		dfsWalk(oldTree,newTree,index,patches)
		return patches;
	}
	
	function dfsWalk(oldNode,newNode,index,patches){
		//�Ա�oldNode��newNode�Ĳ�ͬ����¼����
		patches[index] = [...];
		diffChildren(oldNode.children,newNode.children,index,patches)
	}
	
	//�����ӽڵ�
	function diffChildren(oldChildren,newChildren,index,patches){
		var leftNode =null;
		var currentNodeIndex =index;
		oldChildren.forEach(function(child,i){
			var newChild=newChildren[i];
			currentNodeIndex = (leftNode && leftNode.count)  //����ڵ�ı�־
			? currentNodeIndex + leftNode.count + 1
			: currentNodeIndex + 1;
			
			dfsWalk(child,newChild,currentNodeIndex,patches); //��ȱ����ӽڵ�
			leftNode =child;
		})
	}
	
```

���磬�����div���µ�div�в��죬��ǰ�ı����0����ô��

```
	patches[0] = [{difference}, {difference}, ...] // ������洢�¾ɽڵ�Ĳ�ͬ
```

#### 4.2.2 ��������

����˵�Ľڵ�Ĳ���ָ����ʲô�أ��� DOM �������ܻ᣺

1. �滻��ԭ���Ľڵ㣬����������div������section
2. �ƶ���ɾ���������ӽڵ㣬��������div���ӽڵ㣬��p��ul˳�򻥻�
3. �޸��˽ڵ������
4. �޸��˽ڵ���ı�

���Ƕ����˼��ֲ������ͣ�

 ```
	var REPLACE = 0
	var REORDER = 1
	var PROPS = 2
	var TEXT = 3
 ```
 
 ���ڽڵ��滻���ܼ򵥡��ж��¾ɽڵ��tagName���ǲ���һ���ģ������һ����˵����Ҫ�滻������div����section���ͼ�¼�£�
 
 ```
	patches[0] = [{
		type:REPLACE,
		node:newNode  //el('section',props,children)
	}]
 ```

 ���ڽڵ��������ԣ���idΪcontainer��
 
 ```
	patches[0] = [{
		type:REPLACE,
		node:newNode  //el('section',props,children)
	},{
		type:PROPS,
		props:{
			id:"container"
		}
	}]
 ```

 ������ı��ڵ㣬��������ı��ڵ�2���ͼ�¼�£�
 
 ```
	patches[2] = [{
		type:TEXT,
		content:"Virtual DOM2"
	}]
 ```
 
 ���������div���ӽڵ����������أ�����p, ul, div��˳�򻻳���div, p, ul���������ô�Աȣ��������ͬ�㼶����˳��ԱȵĻ������Ƕ��ᱻ�滻������p��div��tagName��ͬ��p�ᱻdiv����������գ������ڵ㶼�ᱻ�滻������DOM�����ͷǳ��󡣶�ʵ�����ǲ���Ҫ�滻�ڵ㣬��ֻ��Ҫ�����ڵ��ƶ��Ϳ��Դﵽ������ֻ��֪����ô�����ƶ���
 
 ��ǣ�浽�����б�ĶԱ��㷨����Ҫ������һ��С�������ۡ�
 
 #### 4.2.3 �б�Ա��㷨
 
 �������ڿ���Ӣ����ĸΨһ�ر�ʶÿһ���ӽڵ㣺
 
	�ɵĽڵ�˳��
	
	```
		a b c d e f g h i
	```
	
	���ڶԽڵ������ɾ�������롢�ƶ��Ĳ���������j�ڵ㣬ɾ��e�ڵ㣬�ƶ�h�ڵ㣺
	
	```
		a b c h d f g i j
	```

����֪�����¾ɵ�˳������С�Ĳ��롢ɾ���������ƶ����Կ�����ɾ���Ͳ�������Ľ�ϣ������������������ʵ���ַ�������С�༭�������⣨Edition Distance��������Ľ���㷨�� Levenshtein Distance��ͨ����̬�滮��⣬ʱ�临�Ӷ�Ϊ O(M * N)���������ǲ�����Ҫ��Ĵﵽ��С�Ĳ���������ֻ��Ҫ�Ż�һЩ�Ƚϳ������ƶ����������һ��DOM���������㷨ʱ�临�Ӷȴﵽ���Եģ�O(max(M, N))�������㷨ϸ�ڱȽ϶࣬���ﲻ����������Ȥ���Բο�[����](https://github.com/livoras/list-diff/blob/master/lib/diff.js)��

�����ܹ���ȡ��ĳ�����ڵ���ӽڵ�Ĳ������Ϳ��Լ�¼������

```
	patches[0] = [{
		type:REORDER,
		moves:[{ remove or insert },{remove or insert}]
	}]
```

����Ҫע����ǣ���ΪtagName�ǿ��ظ��ģ���������������жԱȡ�������Ҫ���ӽڵ����Ψһ��ʶkey���б�Աȵ�ʱ��ʹ��key���жԱȣ��������ܸ����ϵ� DOM ���ϵĽڵ㡣

���������ǾͿ���ͨ��������ȱ�����������ÿ��Ľڵ���жԱȣ���¼��ÿ���ڵ�Ĳ����ˡ����� diff �㷨����ɼ� [diff.js](https://github.com/livoras/simple-virtual-dom/blob/master/lib/diff.js)��

### 4.3 ���������Ѳ���Ӧ�õ�������DOM����

��Ϊ����һ�������� JavaScript ��������render����������DOM������Ϣ���ṹ��һ���ġ��������ǿ��Զ��ǿ�DOM��Ҳ����������ȵı�����������ʱ��Ӳ�������ɵ�patches�������ҳ���ǰ�����Ľڵ���죬Ȼ����� DOM ������

```
	function patch(node,patches){
		var walker ={index:0}
		dfsWalk(node,walker,patches)
	}
	
	function dfsWalk(node,walker,patches){
		var currentPatches =patches[walker.index] //��pathes�Ǵ���ǰ�ڵ�Ĳ���
		
		var len =node.childNodes? node.childNodes.length : 0;
		for(var i =0;i<len;i++){
			var child =node.childNodes[i];
			walker.index ++;
			dfsWalk(child,walker,patches)
		}
		
		if(currentPatches){
			applyPatches(node,currentPatches)  //�Ե�ǰ�ڵ����DOM����
		}
	}
```

applyPatches,���ݲ�ͬ���͵Ĳ���Ե�ǰ�ڵ����DOM������

```
	funciton applyPatches(node,currentPatches){
		currentPatches.forEach(fucntion(currentPatch){
			switch(currentPatch.type){
				case REPLACE:
					node.parentNode.replaceChild(currentPatch.node.render(),node)
					break
				case REORDER:
					reorderChildren(node,currentPath.moves)
					break
				case PROPS:
					setProps(node,currentPatch.props)
					break
				case TEXT:
					node.textContent =currentPatch.content
					break
				default:
					throw new Error('Unknown patch type ' +currentPatch.type)
			}
		})
	}
```

��������ɼ�[patch.js](https://github.com/livoras/simple-virtual-dom/blob/master/lib/patch.js)

## С��

Virtual DOM �㷨��Ҫ��ʵ�����沽�������������element��diff��patch��Ȼ��Ϳ���ʵ�ʵĽ���ʹ�ã�

```
	// 1. ��������DOM
	var tree = el('div', {'id': 'container'}, [
		el('h1', {style: 'color: blue'}, ['simple virtal dom']),
		el('p', ['Hello, virtual-dom']),
		el('ul', [el('li')])
	])
	
	// 2. ͨ������DOM����������DOM
	var root = tree.render()
	document.body.appendChild(root)
	
	// 3. �����µ�����DOM
	var newTree = el('div', {'id': 'container'}, [
		el('h1', {style: 'color: red'}, ['simple virtal dom']),
		el('p', ['Hello, virtual-dom']),
		el('ul', [el('li'), el('li')])
	])
	
	// 4. �Ƚ���������DOM���Ĳ�ͬ
	var patches = diff(tree, newTree)
	
	// 5. ��������DOMԪ����Ӧ�ñ��
	patch(root, patches)
```

��Ȼ���Ƿǳ��ֲڵ�ʵ����ʵ���л���Ҫ�����¼������ȣ��������� DOM ��ʱ��Ҳ���Լ��� JSX �﷨����Щ���鶼���˵Ļ����Ϳ��Թ���һ���򵥵�ReactJS�ˡ�




























