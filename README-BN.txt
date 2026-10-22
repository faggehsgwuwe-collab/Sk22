SK MUZAMMEL TOURNAMENT — Android APK Builder

এই প্রজেক্ট GitHub Actions দিয়ে একটি Android debug APK তৈরি করে।

গুরুত্বপূর্ণ:
1. GitHub Pages URL বর্তমানে MainActivity.java-তে এইভাবে সেট করা আছে:
   https://faggehsgwuwe-collab.github.io/sk-muzammel-tournament/
   আপনার Pages URL আলাদা হলে MainActivity.java-তে APP_URL বদলান।
2. GitHub repository-র মূল ফোল্ডারে এই প্রজেক্টের সব ফাইল/ফোল্ডার আপলোড করুন।
   আগে থাকা index.html, firebase-messaging-sw.js, manifest.webmanifest ও icons ফাইল মুছবেন না।
3. .github/workflows/build-apk.yml অবশ্যই এই সঠিক ফোল্ডারে থাকবে।
4. GitHub → Actions → Build Android APK → Run workflow চালান।
5. সফল হলে workflow run-এর Artifacts থেকে tournament-debug-apk.zip ডাউনলোড করে extract করুন।
6. app-debug.apk ফোনে ইনস্টল করুন। এটি debug build, Play Store release build নয়।

নোটিফিকেশন সীমাবদ্ধতা:
এই প্রজেক্ট Android 13+ এ POST_NOTIFICATIONS permission চায়। কিন্তু শুধু permission মানেই Firebase push notifications কাজ করা নয়। বর্তমান APK WebView-তে GitHub Pages ওয়েবসাইট খোলে; native Firebase Cloud Messaging receiver যোগ করা হয়নি। ওয়েব পেজের Firebase Web Push service worker WebView-এর ভিতরে সব Android push আচরণ সমর্থন নাও করতে পারে। বাস্তব background push দরকার হলে native FCM SDK, google-services.json এবং Firebase project configuration আলাদাভাবে যোগ করতে হবে।

সিকিউরিটি: Firebase Admin service-account JSON/key কখনো GitHub-এ আপলোড করবেন না।
