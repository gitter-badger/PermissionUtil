# PermissionUtil
###What is this?

[![Join the chat at https://gitter.im/kayvannj/PermissionUtil](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/kayvannj/PermissionUtil?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
A simple wrapper around Android 6.0 runtime permission api
###Why?
Adding runtime permissions is not hard but having to seperate your code and move the methods around to capture callbacks is a little pain. This library provides a chained api to do all you need to do for supporting runtime permissions.

###How?
Anywhere in your ```AppCompatActivity``` that you want to ask for user's permisssion
```java
mRequestObject = PermissionUtil.with(this)
                                .request(Manifest.permission.READ_CONTACTS)
                                .onGrant(
                                    new Func() {
                                        @Override protected void call() {
                                            //Happy Path
                                        }
                                    })
                                .onDeny(
                                    new Func() {
                                        @Override protected void call() {
                                            //Sad Path
                                        }
                                    })
                                .ask(REQUEST_CODE);
```
And add this to ```onRequestPermissionsResult```
```java
mRequestObject.onRequestPermissionsResult(requestCode, permissions, grantResults);
```
###Dependency?
```groovy
compile 'com.android.support:appcompat-v7:23.1.0'
```
###Download
```groovy
compile 'com.github.kayvannj.util.permission:library:1.0.0@aar'
```


License
-------

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


