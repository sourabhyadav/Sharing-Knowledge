So basically things are a bit straight forward.  
Say take an example of an Instagram like application:  

Front-end --> In Android it is coded in .xml files and in Web coded in .html files
Here all the UI and UX related things would be written 
Like making buttons, screen layouts, themes, etc.
 
Understanding the events on UI interactions will be done by: In Android we have onEventListeners like onClickEvent, onCaptureEvent, etc. and in Web, it is handled by JavaScripts like (Angular JS, Node JS, etc.)
OnButtonPress, drag-n-drop, dialogue boxes, etc.
  Screen coordinates, UI parent-child relationships, etc.

In Java, we would have written the main logic or core engine. In Web, we need REST APIs to map or interface for your EventListners to interact with your Event Listeners to core Java logical engine. However, in Android, it is being done by inbuilt Handlers to do so. In android, Google has provided almost all sorts of Handlers which are directly written in Java itself.

The above is similar to something similar to JNI. Say your main engine is written in C/C++. Now you want to pass data or interact with your Java code with C code we have to make use of Java Native Interface APIs to make this possible.

If you want to interact with a Database like MySQL, Django etc. we need to make use of DAVE APIs to create or act as an interface between Java and Database. So basically in Java, we need to call proper Database API to interact with Databases such as add field, modify a field, search, sort, backup, etc.
