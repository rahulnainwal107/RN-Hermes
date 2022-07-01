# RN-Hermes

<b>What is hermes?</b></br>
Hermes is an open-source JavaScript engine optimized for React Native. For many apps, enabling Hermes will result in improved start-up time (Hermes-powered apps launch faster, thanks to build-time precompilation of JavaScript into efficient bytecode.), Hermes is small in APK size, lean on memory, and starts instantly. It won't weigh your app down.</br>
<li>
Initially available with react-native version 0.60.4 and only available for android.
</li>
<li>
With react-native 0.64, Hermes also runs on iOS.
</li>
<li>Android app bundles are supported from React Native 0.62 and up.</li>
<li>
By default, you will be using Hermes if you're on the New Architecture which is available with react-native 0.68 onwards. By specifying a value such as true or false you can enable/disable Hermes as you wish.
</li>
<li>
Starting with React Native 0.69.0, every version of React Native will come with a bundled version of Hermes. We will be building a version of Hermes for you whenever we release a new version of React Native. This will make sure you're consuming a version of Hermes which is fully compatible with the version of React Native you're using.
</li>

# Enabling Hermes

<b>Android</b>
<li>
Edit your android/app/build.gradle file and make the change illustrated below:
</li>
<pre><code>
project.ext.react = [
      entryFile: "index.js",
-     enableHermes: false  // clean and rebuild if changing
+     enableHermes: true  // clean and rebuild if changing
  ] 
</pre></code>
<li>
Also, if you're using ProGuard, you will need to add these rules in proguard-rules.pro :
</li>
<pre><code>
-keep class com.facebook.hermes.unicode.** { *; }
-keep class com.facebook.jni.** { *; }
</pre></code>
<li>
Next, if you've already built your app at least once, clean the build:
</li>
<pre><code>$ cd android && ./gradlew clean</pre></code>
<li>
That's it! You should now be able to develop and deploy your app as usual:
</li>
<pre><code>$ npx react-native run-android</pre></code>

<b>iOS</b>
<li>To enable Hermes for iOS, edit your ios/Podfile file and make the change illustrated below:</li>
<pre><code>
use_react_native!(
     :path => config[:reactNativePath],
     # to enable hermes on iOS, change `false` to `true` and then install pods
     # By default, Hermes is disabled on Old Architecture, and enabled on New Architecture.
     # You can enable/disable it manually by replacing `flags[:hermes_enabled]` with `true` or `false`.
-    :hermes_enabled => flags[:hermes_enabled],
+    :hermes_enabled => true
   )
</pre></code>
<li>Once you've configured it, you can install the Hermes pods with:</li>
<pre><code>$ cd ios && pod install</pre></code>

# More about hermes

<a>https://reactnative.dev/docs/hermes</a><br>
<a>https://hermesengine.dev/</a>
