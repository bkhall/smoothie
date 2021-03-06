NOTE: Smoothie is currently just a draft API. Although the library is fairly
funcional, this is still alpha-quality code. Do not rely on it for production
code. Feedback is very welcome!

What is it?
===========

Easy async loading for Android's ListView/GridView.

Features
========

* Tiny API to implement asynchonous loading of items in Android's
  ListView and GridView.
* Tight integration between user interaction and async loading of items i.e.
  stops loading items on fling, enables loading when panning with finger
  down, etc.
* Prefetch items beyond the currently visible items to reduce the number of
  placeholder items while scrolling (under development).

How do I use it?
================

1. Add Smoothie's jar as a dependency to your project.

2. Implement an ItemEngine. You're only required to override two methods:
   `loadItem()` and `displayItem()`. You can override more methods if you
   want to handle loading items from memory, preloading items, resetting
   item views, etc.

3. On Activity/Fragment creation, attach a Smoothie instance to your
   ListView/GridView:

   ```java
   Smoothie.Builder builder = new Smoothie.Builder(yourListOrGridView, yourItemEngine);
   builder.setPreloadItemsEnabled(true).setPreloadItemsCount(5);
   builder.setThreadPoolSize(4);
   Smoothie s = builder.build();
   ```

4. On your adapter's `getView()`, call Smoothie's `loadItem()` passing the item
   view and the parameters necessary to load the item asynchronously.

The sample app has an example of an ItemEngine powered by
[Android-BitmapCache](https://github.com/chrisbanes/Android-BitmapCache) that
fades images in as they finish loading on a ListView.

Want to help?
=============

Here's a list of pending stuff on the library:

* Proper prefetch support with a custom priority queue on ItemLoader's executor
  service.

File new issues to discuss specific aspects of the API and to propose new
features.

License
=======

    Copyright 2012 Lucas Rocha

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
