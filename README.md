# startActivityForResult
By using startActivityForResult(Intent intent, int requestCode) you can start another Activity and then receive a result from that Activity in the onActivityResult(int requestCode, int resultCode, Intent data) method. The result will be returned as an Intent.
In this example MainActivity will start a DetailActivity and then expect a result from it. Each request type should have its own int request code, so that in the overridden onActivityResult(int requestCode, int resultCode, Intent data) method in MainActivity , it can be determined which request to process by comparing values of requestCode and  REQUEST_CODE_EXAMPLE (though in this example, there is only one).

A few things you need to be aware of:
* Data is only returned once you call finish(). You need to call setResult() before calling finish(), otherwise, no result will be returned.
* Make sure your Activity is not using android:launchMode="singleTask", or it will cause the Activity to run in a separate task and therefore you will not receive a result from it. If your Activity uses singleTask as launch mode, it will call onActivityResult() immediately with a result code of Activity.RESULT_CANCELED.
* Be careful when using android:launchMode="singleInstance". On devices before Lollipop (Android 5.0, API Level 21), Activities will not return a result.
* You can use explicit or implicit intents when you call startActivityForResult(). When starting one of your own activities to receive a result, you should use an explicit intent to ensure that you receive the expected result. An explicit intent is always delivered to its target, no matter what it contains; the filter is not consulted. But an implicit intent is delivered to a component only if it can pass through one of the component's filters.

>> source (stackoverflow's documentation): https://stackoverflow.com/documentation/android/103/intent#t=201706020946147606548
