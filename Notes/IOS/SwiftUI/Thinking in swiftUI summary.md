---
dateCreated: "2022-04-27 15:46"
tags: [swiftUI,swift,ios]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Notes: 

# [[Thinking in swiftUI summary]]

## Overview 
swiftUI is a radical conceptual departure from the previous way of developing apps on Apple's platforms, and it requires you to rethink how to translate an idea you have in mind into this new system.

## View Construction 
To construct views in SwiftUI, you create a tree of view values that describe what should
be onscreen. To change what’s onscreen, you modify state, and a new tree of view values
is computed. SwiftUI then updates the screen to reflect these new view values.

let write an example for a counter application and explain whats going on : 

``` swift
import SwiftUI

struct ContentView: View {
@State var counter = 0
var body: some View {
VStack {	
  Button(action: { counter += 1 }, label: {
	Text("Tap me!")
	.padding()
	.background(Color(.tertiarySystemFill))
	.cornerRadius(5)
})

  if counter > 0 {
   Text("You've tapped A(counter) times")
   } else {
   Text("You've not yet tapped")
   }
  }
 }
}
```

The ContentView contains a vertical stack ([[VStack]]) with two nested views: a button, which increments the counter property when it’s tapped, and a text label that shows either the number of taps or a placeholder text.

notice that the button's action closure does not change the tap count [[Text]] view directly. the closure does not have a reference to that and even if it had, modifying it after the view is presented will not change the presentation. Instead, we need to modify our state 
(in this case the [[@State]] counter variable).
this causes SwiftUI to call the view's body, generating a new description of the view with the new value of counter.

lets talk about the body property, `var body: some View`  this does not tell us much about the view tree that we see on screen, its only says that whatever is being constructed definitely conforms to the [[View]] protocol. the real type of the body looks like this: 


![[Pasted image 20220427162048.png]]

That’s a huge type with lots of generic parameters — and it immediately explains why a construct like some View (an [[opaque type]]) is required for abstracting away these
complicated view types. 

here is the view above as a tree diagram :
![[Pasted image 20220427163657.png]]

the body var contains the structure of the entire view tree- not just the part that on screen at the moment, but all views that could ever be onscreen during the app's lifecycle. when we create a condition 
(`if counter > 0`)  the if statement create has been encoded as a value of type _ConditionalContent_, which contains the type of both branches. 

**but how it is possible? the views are not evaluated at runtime?**
to make this possible, SwiftUI leverages a swift feature called [[function builders]].  
