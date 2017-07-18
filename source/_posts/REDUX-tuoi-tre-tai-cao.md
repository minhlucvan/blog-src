---
title: REDUX tuổi trẻ tài cao
date: 2016-06-28 22:15:25
tags:
	- redux
	- framework
	- javascript
	- Flux
categories:
	- công nghệ		
---
{% asset_img redux-1.png "redux" %}

Có một đều còn làm bạn "bối rối" hơn cả Flux chính là phân biệt Flux với Redux, một pattern phảt lấy cảm hứng từ Flux. Bài viết này sẽ chỉ ra những điểm khác biệt giữa hài pattern này.

nếu bạn chưa đọc bài giới thiệu về Flux, bạn nên đọc qua trước khi đọc bài viết này.

<!--more-->

Redux được tạo ra để giải quết các vấn đề giống như Flux cộng thêm một số thư khác. 

cũng như Flux, Redux sinh ra để quản lý các trạng thái của ứng dụng, làm cho các trạng thái trở nên dễ tiên đoán hơn (predictable). Nếu bạn muốn thay đổi trạn thái bạn buộc phải phun ra một action. Bạn sẽ không thể thay đổi thạng thái một cách trực tiếp vì phần lưu thạng thái (Store) chỉ có getter không có setters. về cơ bản thì Redux và Flux thực sự rất giống nhau.

So why a different pattern? Redux creator Dan Abramov saw an opportunity to improve on Flux. He wanted better developer tools. He saw that if you moved a couple of things around, you could make better developer tools possible, but still have the same predictability that Flux gives you.

Vậy điểm khác biệt ở đây là gì? tác giả của Redux @Dan Abramov đã nhìn thấy những tiềm năng của Flux, Ông ấy có một bộ công cụ phát triển tốt hơn, Ông thấy rằng nếu thay đổi một số thứ, bạn có thể có một công cụ hoàn hảo hơn trong khi vẫn có được đầy đủ các tính năng mà Flux đem lại.

@Dan Abramov muốn hot reloading (code và nhìn thấy thay đổi luôn) và time travel debugging (). Nhưng có một số vấn đề khiến cho developer tools khó làm việc với Flux.

> **Vấn đề 1: code của Store không thể reload nếu không xóa trạng thái**

Trong Flux, Strore bao gồm 2 thứ:

1. Trạng thái làm thay thay đổi logic 
2. Trạng thái hiện tại

Chứa cả 2 thứ trong cùng một đối tưọng chính là chìa khóa cho hot reloading. Khi bạn tại lại đối tượng Store để kết quả mà trạng thai thay đổi logic tạo ra, bạn mất trạng thái được gĩư trong Strore, thêm nữa, bạn đã đăng ký một sự kiện  buộc Store lưu trạng thái của phần còn lại của hệ thống.

![](2.png)

**Giải pháp**

Tách biệt hai chức năng, một đối tượng sẽ lưu trạng thái, đối tưọng này không đưọc reload. Một đối tượng khác bàn gồm tất cả các trạng thái thai đổi logic, đối tưọng này có thể đưọc reload nó khống hề giữ trạng thái nào cả.

> **Vấn đề 2: Trạng thái có thể bị ghi đè bởi mỗi một action**

In time travel debugging, you keep track of each version of a state object. That way, you can go back to an earlier state.

Each time the state is changed, you need to add the old state to an array of previous state objects. But because of the way JavaScript works, simply adding the variable to the array won’t work. This doesn’t create a snapshot of the object, it just creates a new pointer to the same object.

To make it work, each version needs to be an entirely separate object so that you aren’t accidentally changing past versions.

![](4.png)

**Solution**
When an action comes in to the store, don’t handle it by changing the state. Instead, copy the state and make changes to the copy.

![](5.png)

> **Problem 3: There aren’t good places for third-party plugins to jump in**

When you’re making developer tools, you need to be able to write them generically. A user should be able to just drop the tool in without having to custom fit their own code around it.

For this to work, you need extension points… places where the code expects to have things added to it.

An example is logging. Let’s say you want to console.log() every action as it comes in, and then console.log() the state that results from it. In Flux, you’d have to subscribe to the dispatcher’s updates and to updates from each store. But that’s custom code, not something a third-party module can easily do.

![](6.png)

**Solution**
Make it easy to wrap parts of the system in other objects. These other objects add their bit of functionality on top of the original. You can see these kinds of extension points in things like “enhancers” or “higher order” objects, as well as middleware.

In addition, use a tree to structure the state change logic. This makes it so the store only emits one event to notify the views that the state has changed. This event comes after the whole state tree has been processed.


![](7.png)
Note: With these problems and solutions, I‘m focusing on the developer tooling use case. These changes help in other use cases, too. On top of that, there are other differences between Redux and Flux. For example, Redux also reduces boilerplate and it makes it easier to reuse logic in the store. Here’s a list of some other upsides to Redux.

So let’s see how Redux makes these things possible.

## The new cast of characters

The new cast of characters

### Action creators

![](8.png)

Redux keeps the action creator from Flux. Whenever you want to change the state of the application, you shoot off an action. That’s the only way that the state should be changed.

As I said in the article on Flux, I think of the action creator as a telegraph operator. You go to the action creator knowing basically what message you want to send, and then the action creator formats that in a way that the rest of the system can understand.

**
Unlike Flux, action creators in Redux do not send the action to the dispatcher. Instead, they return a formatted action object.
**

### The Store

I described stores in Flux as over-controlling bureaucrats. All state changes must be made personally by a store and have to go through the action pipeline, instead of being requested directly. The store in Redux is still controlling and bureaucratic, but it’s a little bit different.

![](9.png)

In Flux, you can have multiple stores. Each store has its own little fiefdom, and it is in total control. It holds on to its little slice of state, and has all the logic for changing that little slice of state.

The Redux store tends to delegate more. And it has to. In Redux, there is only one store… so if it did everything itself, it would be taking on too much work.

Instead, it takes care of holding on to the whole state tree. It then delegates the work of figuring out what state changes need to happen. The reducers, headed up by the root reducer, take on this task.

You might have noticed there’s no dispatcher. That’s because, in a bit of a power grab, the store has also taken over dispatching.

### The reducers

When the store needs to know how an action changes the state, it asks the reducers. The root reducer takes charge and slices the state up based on the state object’s keys. It passes each slice of state to the reducer that knows how to handle it.

![](10.png)

I think of the reducers as a department of white-collar workers who are a little overzealous about photocopying. They don’t want to mess anything up, so they don’t change the state that has been passed in to them. Instead, they make a copy and make all their changes on the copy.

This is one of the key ideas of Redux. The state object isn’t manipulated directly. Instead, each slice is copied and then all of the slices are combined into a new state object.

The reducers pass their copies back to the root reducer, which pastes the copies together to form the updated state object. Then the root reducer sends the new state object back to the store, and the store makes it the new official state.

If you have a small application, you might only have one reducer making a copy of the whole state object and making its changes. Or if you have a large application, you might have a whole tree of reducers. This is another difference between Flux and Redux. In Flux, the stores aren’t necessarily connected to each other and they have a flat structure. In Redux, the reducers are in a heirarchy. This hierarchy can have as many levels as needed, just like the component hierarchy.

### The views: smart and dumb components

Flux has controller views and regular views. The controller views act as middle managers, managing the communication between the store and their child views.

![](11.png)

In Redux, there’s a similar concept: smart and dumb components. The smart components are the managers. They follow a few more rules than the controller views, though:

	- Smart components are in charge of the actions. If a dumb component underneath them needs to trigger an action, the smart component passes a function in via the props. The dumb component can then just treat that as a callback.
	- Smart components do not have their own CSS styles
	- Smart components rarely emit DOM of their own. Instead, they arrange dumb components, which handle laying out DOM elements.

Dumb components don’t depend on action files directly, since all actions are passed in via props. This means that the dumb component can be reused in a different app that has different logic. They also contain the styles that they need to look reasonably good (though you can allow for custom styling — just accept a style prop and merge it in to the default styles).

### The view layer binding

![](12.png)

To connect the store to the views, Redux needs a little help. It needs something to bind the two together. This is called the view layer binding. If you’re using React, this is react-redux.

The view layer binding is kind of like the IT department for the view tree. It makes sure that all of the components can connect to the store. It also takes care of a lot of technical details so that the rest of the hierarchy doesn’t have to understand them.

The view layer binding introduces three concepts:
	1. The Provider component: This is wrapped around the component tree. It makes it easy for the root component’s children to hook up to the store using connect().
	2. connect(): This is a function provided by react-redux. If a component wants to get state updates, it wraps itself using connect(). Then the connect function will set up all the wiring for it, using the selector.
	3. selector: This is a function that you write. It specifies what parts of the state a component needs as properties.

### The root component

![](13.png)

All React applications have root components. This is just the component at the top level of the component hierarchy. But in Redux applications, this component takes on more responsibility.

The role it plays is kind of like a C-level executive. It puts all of the teams in place to tackle the work. It creates the store, telling it what reducer to use, and brings together the view layer binding and the views.

The root component is pretty hands-off after it initializes the app, though. It doesn’t get caught up in the day-to-day concerns of triggering rerenders. It leaves that to the components below it, assisted by the view layer binding.


## How they all work together
Let’s see how these parts work together to create a functioning app.

### The Setup

The different parts of the app need to be wired up together. This happens in setup.

1. **Get the store ready.** The root component creates the store, telling it what root reducer to use, using createStore(). This root reducer already has a team of reducers which report to it. It assembled that team of reducers using combineReducers().

![](14.png)

2. **Set up the communication between the store and the components.*** The root component wraps its subcomponents with the provider component and makes the connection between the store and the provider.

The Provider creates what’s basically a network to update the components. The smart components connect to network using connect(). This ensures they’ll get state updates.

![](15.png)

3. **Prepare the action callbacks.** To make it easier for dumb components to work with actions, the smart components can setup action callbacks by using bindActionCreators(). This way, they can just pass down a callback to the dumb component. The action will be automatically dispatched after it is formatted.

![](16.png)

### The data flow

Now that the application is set up, the user can start interacting with it. Let’s trigger an action to see the data flow.

![](17.png)

1. The view requests an action. The action creator formats it and returns it.

![](18.png)

2. The action is either dispatched automatically (if bindActionCreators() was used in setup), or the view dispatches the action.

![](19.png)

3. The store receives the action. It sends the current state tree and the action to the root reducer.

![](20.png)

4. The root reducer cuts apart the state tree into slices. Then it passes each slice to the subreducer that knows how to deal with it.

![](21.png)

5. The subreducer copies the slice and makes changes to the copy. It returns the copy of the slice to the root reducer.

![](22.png)

6. Once all of the subreducers have returned their slice copies, the root reducer pastes all of them together to form the whole updated state tree, which it returns to the store. The store replaces the old state tree with the new one.

![](23.png)

7. The store tells the view layer binding that there’s new state.

![](24.png)

8. The view layer binding asks the store to send over the new state.

![](25.png)

9. The view layer binding triggers a rerender.

![](26.png)

So that’s how I think of Redux and its differences from Flux. Hope it helps!

## Kết luận

cảm ơn về bài viết rất thú vị đại ca **Lin Clark** và [code-cartoons.com](https://code-cartoons.com/). 

redux là một kiến trúc mới cho tầng view nó được facebook phát triển để giải quết các vấn đề cố hưu của facebook khi dùng MVC. từ xưa đến nay làm việc với font-end sẽ có hai dạng kiến trúc chính:

1. **kiến trúc hướng sự kiện** có nghĩa là sẽ lần lượt đăng kí các sự kiện, khi có sự kiện thì thực thi hoạt động rồi update view. trang nhỏ thì không sao nếu trang lớn và logic phức tạp thì nó trở thành thảm họa cả với UX và DX, đầu tiên bạn sẽ không thể nào phân biệt đc các thành phần cũng như vòng đời của các sự kiện, rồi sẽ ra sao nếu muốn thêm một tác vụ cho sự kiện nào đó. đến một lúc bạn nhìn lại đống sản phẩm của mình và chỉ ước mình có thể đập đi xây lại từ đầu. :D

2. **kiến trúc MVC** đây là kiến trúc kinh điển với các developer rồi nhưng với chỉ view layer thì MVC dường như không đủ. với font-end quan hệ giữa M-C phức tạp hơn back-end. 

(to be continue)
...

nguồn: https://code-cartoons.com/a-cartoon-intro-to-redux-3afb775501a6#.5cx9cs5s4