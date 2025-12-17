---

title: Android SDK V6
date: 2022-05-19 18:44:29
permalink: /pages/e2eeda/
categories:

* Text-based API
* Channel Access

tags:

* null

author: 
  name: Sobot 
  link: https://www.sobot.com

---

# Android SDK V6

Sobot SDK Visitor Side provides enterprises with a complete set of intelligent agent solutions. Sobot Agent SDK includes both agent business logic and interactive interfaces. Enterprises only need two simple steps to integrate Sobot Agent into their APP, enabling the APP to have 7 * 24 hours of agent service capability.

The administrator can add an APP in the background under "Homepage - Online Agent - Settings - Channel Integration Settings - Add Channel", and then complete the SDK integration according to the instructions in this document.

Sobot agent SDK has the following features:

* Online consultation: Chatbot, Live agent, Leave a message, Help center.  
* Assign to a specific skill group.  
* Guide users to leave a message when queuing or agents are offline.  
* Hide the transfer-to-agent button in bot-first mode; show it after N unknown bot responses.  
* Agent satisfaction rating: User-initiated rating + Prompt upon exit.  
* Pass user data: User ID + Basic info + Custom fields.  
* Pass product source page: Page title + Page URL.  
* Highly customizable UI.

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-0.png)

Relevant restrictions and precautions:

1. The Android SDK supports Android system version 5.0 (API 21) and above, and works in both portrait and landscape modes.

2. It is recommended to upgrade the development tool Android Studio to version 3.0 or above.

3. The Android SDK needs to request storage, microphone, and camera permissions. Otherwise, some features will not work.

#### Document Introduction

##### ● Integration Process Diagram

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-1-1.png)

##### ● File Description

**SDK files include** **SDK source code package (sobotsdk_x)** **,** **Demo source code (Sobot_Sdk_Demo_Android_V6)** **, and** **Doc** **related documentation.**

| File | Description | 
|:----|:----|
| ZCSobotApi   | This file provides access functions   | 
| Information   | Startup configuration information param class   |

#### Integration Method

##### ● Import Integration

Download link: [Android_SDK_V6](https://shimo.im/docs/ZzkLVP1x4wS2Qo3Q)

Import Module:

Unzip the downloaded Sobot Android_SDK_XXX.zip file, copy the sobotsdk-x file directly into your project, then click Build --> Clean Project. After that, add the project dependency in build.gradle.

After completing the steps above, the build.gradle file will look like this:

```js
dependencies {
      implementation project(':sobotsdk-x')
      implementation 'com.squareup.okhttp3:okhttp:4.4.0'
      implementation 'androidx.appcompat:appcompat:1.0.0'
      implementation 'androidx.recyclerview:recyclerview:1.0.0'
      //Currently supports several common image loading libraries. You must choose one from the following image loading libraries to add a dependency.
      //implementation 'com.nostra13.universalimageloader:universal-image-loader:1.9.5'
      //implementation 'com.squareup.picasso:picasso:2.71828'
      //implementation 'com.facebook.fresco:fresco:2.6.0'
      implementation 'com.github.bumptech.glide:glide:4.9.0'
}
```

[Notice]

If you are using the picasso framework, starting from version 4.1.4, the SDK supports version 2.71828 and above by default.

If you are using the Glide v4 framework, starting from version 4.1.4, the SDK supports version 4.9.0 and above by default.

If you are using an SDK version earlier than 4.1.4, but Glide v4 is using a version above 4.9.0, you still need to add the dependency separately: 'com.sobot.chat:sobotsupport-glidev4:2.3'.

If you want to use your own image loading method, you can use the following approach: SobotBitmapUtil.setImageLoader(new SobotImageLoader() {}); After using this method, network images will not use the image loading method inside the SDK when displayed.

##### ● Dependency Integration

[Latest version address](https://central.sonatype.com/artifact/com.sobot.chat/sobotsdk_x)

```js
implementation  'com.sobot.chat:sobotsdk_x:+'
```

In build.gradle, as shown below:

```js
dependencies {
      implementation 'com.sobot.chat:sobotsdk_x:+'
      implementation 'com.squareup.okhttp3:okhttp:4.4.0'
      implementation 'androidx.appcompat:appcompat:1.0.0'
      implementation 'androidx.recyclerview:recyclerview:1.0.0'
      //Currently supports several common image loading libraries. You must choose one from the following image loading libraries to add dependency.
      //implementation 'com.nostra13.universalimageloader:universal-image-loader:1.9.5'
      //implementation 'com.squareup.picasso:picasso:2.71828'
      //implementation 'com.facebook.fresco:fresco:2.6.0'
      implementation 'com.github.bumptech.glide:glide:4.9.0'
}
```

[Notice]

If you are using the picasso framework, starting from version 4.1.4, the SDK supports version 2.71828 and above by default.

If you are using the Glide V4 framework, starting from version 4.1.4, the SDK supports version 4.9.0 and above by default.

If you are using an SDK version earlier than 4.1.4, but glide v4 is using a version above 4.9.0, you still need to add the dependency separately: 'com.sobot.chat:sobotsupport-glidev4:2.3'.

If you want to use your own image loading method, you can use the following approach: SobotBitmapUtil.setImageLoader(new SobotImageLoader() {}); After using this method, network images will not use the image loading method inside the SDK when displayed.

Obfuscation related:

Refer to the obfuscation configuration in the obfuscation file (Android_SDK_x.x.x\Sobot_Sdk_Demo_Android_V6\sobotsdkdemo\proguard-rules.pro) to add obfuscation rules.

```
#Sobot SDK
-keep class com.sobot.chat.** {*;}
-dontwarn com.sobot.chat.**
```

Note: The image framework used requires self-configuration for obfuscation.

#### Quick Start

##### ● Domain Settings

Domain Name Description:

* The default SaaS platform domain name is: https://api.sobot.com.
* If you are using Tencent Cloud services, set it to: https://www.soboten.com.
* If you are using a localized deployment, use your own service domain name.

Example code:

[Note: The domain name must be set before all API requests, that is, it must be set before initialization.]

```js
SobotBaseUrl.setApi_Host("Domain");
```

##### ● Get Appkey

Log in to the [Sobot Management Platform](https://www.sobot.com/auth/sign_in) to retrieve, as shown in the picture.

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-3-2.png)

##### ● Initialization

Initialization of param and calling method:

**[Note: Before starting the Sobot SDK, you need to call the initialization method initSobotSDK. Otherwise, the SDK will not start.]**

**[Note: The invocation of other functions in ZCSobotApi needs to be carried out after the initialization method is completed, otherwise it will not take effect.] **

API ：

```js
/**
* Initialize sdk
* @param applicationcontext Context Required
* @param appkey User's appkey Required. If the user is a platform version, pass the headquarter's appkey
* @param partnerid     User's unique identifier. Do not pass the same value. Can be empty
*/
ZCSobotApi.initSobotSDK(Context application,String appkey,final String partnerid);
```

Example code:

```js
private void initSobotApp() {  
      ZCSobotApi.initSobotSDK(your application,"your appkey", "");
}
```

##### ● Launch Sobot Page

###### 1. Launch The Sobot Page

API 

```js
Information info = new Information();
//appkey is required
info.setApp_key("Your appkey");
/**
* @param context Context object
* @param information Initialization parameter 
*/
ZCSobotApi.openZCChat(context, information);
```

Example code:

```js
Information info = new Information();
// appkey is required
info.setApp_key(et_appkey.getText().toString());
// Note: Unique user identifier. Do not pass the same value. Optional, maximum length is 300.
info.setPartnerid("");
// User nickname. Optional.
info.setUser_nick("");
// User name. Optional.
info.setUser_name("");
// User phone. Optional.
info.setUser_tels("");
// User email. Optional.
info.setUser_emails("");
// Custom avatar. Optional.
info.setFace("");
// User QQ. Optional.
info.setQq("");
// User remark. Optional.
info.setRemark("");
// Landing page title. Optional.
info.setVisit_title("");
// Landing page URL. Optional.
info.setVisit_url("");
// Company name. Added in version 4.1.5.
info.setEnterprise_name("xxx");
ZCSobotApi.openZCChat(context, info);
```

If there are special requirements, the SDK also provides a way to integrate the chat interface by embedding it as a Fragment. This allows developers to use the SDK more flexibly. See the example code below (you can also refer to the implementation of Fragment in SobotChatActivity).

```js
Bundle informationBundle = new Bundle();
informationBundle.putSerializable(ZhiChiConstant.SOBOT_BUNDLE_INFO, info);
SobotChatFragment fragment = SobotChatFragment.newInstance(informationBundle);
FragmentManager fm = getSupportFragmentManager();
FragmentTransaction transaction = fm.beginTransaction();
// containerId is the resId of ViewGroup
transaction.replace(containerId, fragment);
try {
    transaction.commitAllowingStateLoss();
} catch (Exception e) {
}
```

###### 2. Start The Customer Service Center

```js
Information info = new Information();
info.setApp_key("Your AppKey");  // The secret key assigned to the App

// The agent center phone button will only display if both the phone number and display text are not empty
info.setHelpCenterTel("18510000000"); // Phone number
info.setHelpCenterTelTitle("Contact Number"); // Display text for the call button

/**
* @param context Context object
* @param information Initialization parameter 
*/
ZCSobotApi.openZCServiceCenter(context, information);
```

The effect picture is as follows:

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-3-5.png)

##### ● end chat 

When a user logs out of the application, the SDK's logout operation can be called (this should be called when switching accounts). This operation will notify the server to unbind the push notifications, preventing the situation where the user has logged out but push notifications are still sent to the current device.

Call the following method when the user logs out:

[Note: Calling this method will cause the channel connection to break. At this time, the user will no longer be able to receive messages.]

```js
/**
* @param context Context object
* @param reason End reason, can be empty
*/
ZCSobotApi.outCurrentUserZCLibInfo(context,reason);
```

#### Function Description

##### ●Permission Description

The SDK uses 3 high-sensitivity permissions (file storage, microphone, camera).

Permission Usage Description Table:

|  Permission  | Functions involving this permission |
|:----|:----|
| File Storage | Click on pictures, videos inside the plus sign; Upload pictures, videos in messages; |
| Microphone | Send voice messages to agent; Take videos inside the plus sign; |
| Camera  | Take videos inside the plus sign; Take photos in messages; |

* These high-sensitivity permissions are only used in the functions listed in the table above. They are dynamically checked and requested when in use, and can only proceed after the user agrees. The absence of these high-sensitivity permissions does not affect the normal use of other functions in the SDK.

##### ● bot agent 

###### 1. Custom Access Mode

Based on the needs of your own business, you can configure the following initialization param to control the access mode:

```js
// Whether to use voice function true for use, false for not use. Default is true.
info.setUseVoice(true);
// Whether to use bot voice function true for use, false for not use. Default is false. Requires payment to use.
info.setUseRobotVoice(false);
// Agent mode control -1 no control, run according to the mode set in the server backend.
// 1 Only bot, 2 Only human, 3 Bot first, 4 Human priority.
info.setService_mode(-1);
```

###### 2. Customize Trans-to-agent Event

The SDK can configure the trans-to-agent interceptor to perform additional logic processing before trans-to-agent, such as custom skill group selection in Dialog.

1. Set up the interceptor

```js
SobotOption.transferOperatorInterceptor = new SobotTransferOperatorInterceptor() {
    @Override
    public void onTransferStart(final Context context, final SobotTransferOperatorParam param) {
        //do something
    }
};
```

2. Modify the trans-to-agent parameter SobotTransferOperatorParam. The following is an introduction to the modifiable parameters:

```js
//skill group ID 
String groupId;
//skill group name
String groupName;
//whether to show tips after trans-to-agent
boolean isShowTips;
//product card information
ConsultingContent consultingContent;
```

3. Use the trans-to-agent param to actively call the trans-to-agent API:

```js
/**
 * External active call to trans-to-agent 
 * @param context
 * @param param trans-to-agent param         
 */
ZCSobotApi.connectCustomerService(context, param);
```

##### ● Human Agent

###### 1. Connect To The Specified Skill Group

Get the skill group number in the background:

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-1.png)

Configure the skill group ID in the SDK code:

```js
//Preset skill group ID
info.setGroupid("your groupId");
//Preset skill group name, optional
info.setGroup_name("your groupName");
```

Note: This field is optional. If you pass the skill group ID, then after the SDK internally trans-to-agent, the skill group selection box will not pop up. It will directly jump to the skill group corresponding to the passed ID.

###### 2. Connect To The Specified Agent

Get the specified agent ID in the background:

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-2.png)

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-2-1.png)

Set in the SDK code:

```js
// Transfer type (0 - Can transfer to other agent, 1 - Must transfer to specified agent)
info.setTranReceptionistFlag(1);
// Specified agent id
info.setChoose_adminid("your Customer service id");
```

Attention:

Choose_adminid: Specifies the agent to connect to. If not set, the default will be used.

TranReceptionistFlag: Set whether it must be transferred to the specified agent after assigning a specific agent. 0: Can be transferred to other agents, 1: Must be transferred to the specified agent. Note: If set to 1, when the specified agent is offline, it cannot be transferred to other agents.

###### 3. Set Up User-defined Profiles And Custom Fields

Developers can directly pass in these user information for the agent to view.

Configure the fields you need to display on the workbench by yourself. The configuration method is shown in the figure below:

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-3.png)

```js
//Set user custom fields, key must be the ID corresponding to the backend field
Map<String,String> customerFields = new HashMap<>();
customerFields.put("weixin","your wechat");
customerFields.put("weibo","your weibo");
customerFields.put("sex","female");
customerFields.put("birthday","2017-05-17");
info.setCustomer_fields(customerFields);
```

User-defined profile

Method 1: Map Method

```js
//Custom user information
Map<String, String> customInfo = new HashMap<>();
customInfo.put("Information", "aaaaa");
info.setParams(customInfo);
```

Method Two: Json Method

```js
//Custom user data. The string must be in JSON format, otherwise it may not display correctly.
info.setParams("{\"title\":\"Title\",\"url\":\"https://www.baidu.com\"}");
```

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-3-1.png)

###### 4. Set To Send A Message Automatically After A Successful Transfer

The SDK can be set to automatically send a message after a successful transfer. You can choose whether to send it every time you enter the chat page. By default, it sends only once.

```js
//Send text message
//Set sending mode 
//SobotAutoSendMsgMode.Default Default, do not send
//SobotAutoSendMsgMode.SendToRobot Send to bot only
//SobotAutoSendMsgMode.SendToOperator   Send to human agent only
//SobotAutoSendMsgMode.SendToAll   Send to all
//setIsEveryTimeAutoSend Whether to send every time when entering the chat page
info.setAutoSendMsgMode(SobotAutoSendMsgMode.SendToAll.setContent("your msg").setIsEveryTimeAutoSend(false));

//After trans-to-agent succeeds, text, images, videos, and files can be sent (only in human mode), requiring setting the local file path and sending type
//SobotAutoSendMsgMode.ZCMessageTypeText Text (default)
//SobotAutoSendMsgMode.ZCMessageTypePhoto Image
//SobotAutoSendMsgMode.ZCMessageTypeFile File
//SobotAutoSendMsgMode.ZCMessageTypeVideo Video
String path = CommonUtils.getSDCardRootPath() + File.separator + "2.jpg";
//path =  "Content to send";
//path =  CommonUtils.getSDCardRootPath() + File.separator + "3.mp4";
//path = CommonUtils.getSDCardRootPath() + File.separator + "1.txt";
info.setAutoSendMsgMode(SobotAutoSendMsgMode.SendToOperator.setContent(path).setAuto_send_msgtype(SobotAutoSendMsgMode.ZCMessageTypePhoto));
```

###### 5. Set Designated Customers To Queue For Priority Access

The SDK can set the current user's queue priority. When this user enters the queue, they will be served first.

```js
//Set queue priority access true:priority access false:default value, normal queue
info.setIs_Queue_First(true);
```

###### 6. Set Up Custom Fields For Service Summary

The SDK can configure custom fields for the service summary. This allows the agent to create service summaries for chats more quickly.

1. Get Custom Field ID

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-6.png)

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-6-1.png)

2. Set the custom field for service summary (trans-to-agent supports passing in the service summary parameter)

```js
//service summary custom fields
Map<String, String> summaryInfo = new HashMap<>();
summaryInfo.put("your keyId", "your value");
info.setSummary_params(summaryInfo);
```

###### 7. Set Up Multi-turn Chat API Param

When using the multi-turn chat feature, for each API, we will pass two fixed custom parameters: uid and multiParams. The uid is the unique identifier of the user, and multiParams is a custom field in JSON string format. If the user has integrated these two fields, we will return them to the third-party API. If not, we will pass empty fields.

```js
// Multi-turn chat custom param
info.setMulti_params("{\"key1\",\"val1\"}");
```

###### 8. Product Inquiry Information And Support For Sending Message Cards Directly, Only Supported In Manual Mode

```js
When users chat with agents, they often need to send product or order inquiries to the agent so that the agent can review them. The inquiry object currently supports up to 5 attributes (title, imgUrl, fromUrl, describe, label), where (title, fromUrl) are required fields. Below is an example using a product:
// Inquiry content
ConsultingContent consultingContent = new ConsultingContent();
// Title of the inquiry content, required
consultingContent.setSobotGoodsTitle("XXX Super TV 50-inch 2D Smart LED Black");
// Image for the inquiry content, optional but must be an image URL
consultingContent.setSobotGoodsImgUrl("http://www.li7.jpg");
// Source page of the inquiry, required
consultingContent.setSobotGoodsFromUrl("www.sobot.com");
// Description, optional
consultingContent.setSobotGoodsDescribe("XXX Super TV S5");
// Label, optional
consultingContent.setSobotGoodsLable("￥2150");
// Whether to auto-send after trans-to-agent
consultingContent.setAutoSend(true);
// Whether to resend every time when returning to the chat page: true means always send, false means send only once (default is once)
consultingContent.setEveryTimeAutoSend(false);
// Start the Sobot agent page and add in Information, trans-to-agent sends card message
info.setConsultingContent(consultingContent);
```

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-8.png)

###### 9. Send Order Card, Only Supported In Manual Mode. The Click Event Of The Order Card Can Be Intercepted.

Usage 1: When starting Sobot agent, automatically send order card messages.

```js
List<OrderCardContentModel.Goods> goodsList = new ArrayList<>();
goodsList.add(new OrderCardContentModel.Goods("Apple", "https://img.sobot.com/chatres/66a522ea3ef944a98af45bac09220861/msg/20190930/7d938872592345caa77eb261b4581509.png"));
goodsList.add(new OrderCardContentModel.Goods("Apple1111111", "https://img.sobot.com/chatres/66a522ea3ef944a98af45bac09220861/msg/20190930/7d938872592345caa77eb261b4581509.png"));
goodsList.add(new OrderCardContentModel.Goods("Apple2222", "https://img.sobot.com/chatres/66a522ea3ef944a98af45bac09220861/msg/20190930/7d938872592345caa77eb261b4581509.png"));
goodsList.add(new OrderCardContentModel.Goods("Apple33333333", "https://img.sobot.com/chatres/66a522ea3ef944a98af45bac09220861/msg/20190930/7d938872592345caa77eb261b4581509.png"));
OrderCardContentModel orderCardContent = new OrderCardContentModel();
//Order number (required)
orderCardContent.setOrderCode("zc32525235425");
//Order status
//Pending payment:1 Awaiting shipment:2 In transit:3 Out for delivery:4 Completed:5 Pending review:6 Cancelled:7
orderCardContent.setOrderStatus(1);

//Custom order status name. Only valid when the order status is 0, other values follow original logic.
//orderCardContent.setOrderStatus(0);
//orderCardContent.setStatusCustom("Your custom status");                 

//Total order amount (in cents)
orderCardContent.setTotalFee(1234);
//Total number of items in the order
orderCardContent.setGoodsCount("4");
//Order link
orderCardContent.setOrderUrl("https://item.jd.com/1765513297.html");
//Order creation time 
orderCardContent.setCreateTime(System.currentTimeMillis() + "");
//Whether to auto-send after transferring to agent
orderCardContent.setAutoSend(true);
//Whether to resend every time when re-entering the chat page. True means always send, false means send only once. Default is send only once.
orderCardContent.setEveryTimeAutoSend(false);
//Order item list
orderCardContent.setGoods(goodsList);
//Order card content
info.setOrderGoodsInfo(orderCardContent);
```

Usage Two: After trans-to-agent, you can add an order button in the plus sign. Click it to send an order message to the agent.

```js
final String ACTION_SEND_ORDERCARD = "sobot_action_send_ordercard";
ChattingPanelUploadView.SobotPlusEntity ordercardEntity = new ChattingPanelUploadView.SobotPlusEntity(ResourceUtils.getDrawableId(getApplicationContext(), "sobot_ordercard_btn_selector"), ResourceUtils.getResString(getApplicationContext(), "sobot_ordercard"), ACTION_SEND_ORDERCARD);
tmpList.add(ordercardEntity);
SobotUIConfig.pulsMenu.operatorMenus = tmpList;
//sSobotPlusMenuListener can only have one listener, otherwise the latter will overwrite the former (for example: 
//If both custom position and order button are added in the plus menu, you can determine which button is clicked based on the action and handle it accordingly)
SobotUIConfig.pulsMenu.sSobotPlusMenuListener = new SobotPlusMenuListener() {
    @Override
    public void onClick(View view, String action) {
        if (ACTION_SEND_ORDERCARD.equals(action)) {
            Context context = view.getContext();
            List<OrderCardContentModel.Goods> goodsList = new ArrayList<>();
            goodsList.add(new OrderCardContentModel.Goods("Apple", "https://img.sobot.com/chatres/66a522ea3ef944a98af45bac09220861/msg/20190930/7d938872592345caa77eb261b4581509.png"));
            OrderCardContentModel orderCardContent = new OrderCardContentModel();
            //Order number (required)
            orderCardContent.setOrderCode("zc32525235425");
            //Order status
            //Pending payment:1 Pending shipment:2 In transit:3 Out for delivery:4 Completed:5 Pending review:6 Cancelled:7
            orderCardContent.setOrderStatus(1);

            //Custom order status name. Only valid when order status is 0, other values follow the original logic
            //orderCardContent.setOrderStatus(0);
            //orderCardContent.setStatusCustom("Your custom status");   

            //Total order amount (unit is cents)
            orderCardContent.setTotalFee(1234);
            //Total number of goods in the order
            orderCardContent.setGoodsCount("4");
            //Order link
            orderCardContent.setOrderUrl("https://item.jd.com/1765513297.html");
            //Order creation time 
            orderCardContent.setCreateTime(System.currentTimeMillis() + "");
            //Whether to send automatically after transferring to an agent
            orderCardContent.setAutoSend(true);
            //Whether to resend every time entering the chat page. True means always send, false means send only once. Default is false.
            orderCardContent.setEveryTimeAutoSend(false);
            //List of goods in the order
            orderCardContent.setGoods(goodsList);
            ZCSobotApi.sendOrderGoodsInfo(context, orderCardContent);
        }
    }
};
```

Configure the order card interception. You can also use ZCSobotApi.setNewHyperlinkListener() for interception. After setOrderCardListener intercepts, setNewHyperlinkListener will not intercept anymore.

```js
ZCSobotApi.setOrderCardListener(new SobotOrderCardListener() {
    @Override
    public void onClickOrderCradMsg(OrderCardContentModel orderCardContent) {
        ToastUtil.showToast(getApplicationContext(), "Clicked the order card" );
    }
});
```

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-2-9.png)

###### 10. Set Whether The User Is A VIP And The User's VIP Level

```js
// Can be set when starting Sobot agent
// Specify whether the customer is VIP, 0: normal 1: VIP
info.setIsVip("1");
// Set VIP level by name; VIP level can be edited in Sobot management end (System Settings > Custom Fields > Customer Fields), get the ID or name corresponding to the level
info.setVip_level("Honorable");
```

###### 11. Set User-Defined Tags

```js
//Can be set when starting Sobot agent
//User tags can be edited in the Sobot management console (System Settings > Custom Fields > Customer Fields), get the ID or name corresponding to the user tag
//Multiple user tags can be added, separate multiple tag IDs or names with a comma
info.setUser_label("Celebrity,Journalist");
```

###### 12. Send Custom Cards To Chat Records, And Recommend Them To Customers In A Systematic Way

[Custom Card Param Description Document](https://shimo.im/docs/LFn2pOwBxCQL6QwI)

```
//1.create SobotChatCustomCard data
SobotChatCustomCard customCard = new SobotChatCustomCard();

//Card id
customCard.setCardId("cardId12121212");

//Recommended display mode, default false. The card can only be sent to the user in manual mode; true means the card can also be sent to the user in machine mode; one chat can only send once
customCard.setShowCustomCardAllMode(true);

//Card type 0, "Order Card", 1, "Product Card"
customCard.setCardType(rg_card_type.getCheckedRadioButtonId() == R.id.rg_dingdan ? 0 : 1);
//Card style 0, "Flat", 1, "List"
customCard.setCardStyle(rg_card_style.getCheckedRadioButtonId() == R.id.rg_pingpu ? 0 : 1);
//Whether to send as customer identity: 0: "System identity", 1: "Customer identity", supported from v4.1.4 version
customCard.setIsCustomerIdentity(0);                          
// Configure top guide text, image, and card description
customCard.setCardDesc("Test description test description test description test description test description test description test description test description test description");
customCard.setCardGuide("Test title guide text test title guide text test title guide text test title guide text test title guide text test title guide text");
customCard.setCardImg("https://hk.sobot.com/auth/_next/static/media/sideZh.74024132.png");
customCard.setCardLink("https://www.sobot.com");

// Configure custom click buttons
List<SobotChatCustomMenu> menus = new ArrayList<>();
SobotChatCustomMenu m = new SobotChatCustomMenu();
m.setMenuLink("Many words Many words Many words Many words");
m.setMenuLinkType(0);
m.setMenuType(2);
m.setMenuName("Send");
m.setMenuTip("Send tip");
menus.add(m);
SobotChatCustomMenu mm = new SobotChatCustomMenu();
mm.setMenuLink("Many words");
mm.setMenuLinkType(2);
mm.setMenuType(1);
mm.setMenuName("Confirm");
mm.setMenuTip("Send tip");
menus.add(mm);
SobotChatCustomMenu mmm = new SobotChatCustomMenu();
mmm.setMenuLink("Many words");
mmm.setMenuLinkType(2);
mmm.setMenuType(0);
mmm.setMenuName("View details many words many words many words many words");
mmm.setMenuTip("Send tip");
menus.add(mmm);
customCard.setCardMenus(menus);

// Configure custom fields
Map<String, Object> param = new HashMap<>();
param.put("Test", "0999999999999990");
customCard.setCustomField(param);

// Configure custom card middle list part
List<SobotChatCustomGoods> goods = new ArrayList<>();
int goodsNum = 3;
for (int i = 0; i < goodsNum; i++) {
    SobotChatCustomGoods g = new SobotChatCustomGoods();
    // Bot standard question, can be "", supported from v4.1.4 version
    g.setCustomCardQuestion("First standard question");
    g.setCustomCardAmount("222.9");
    g.setCustomCardTime("2023-06-25 14:32:21");
    g.setCustomCardCode("sobot121u321u3");
    g.setCustomCardStatus("Pending receipt");
    g.setCustomCardCount("5");
    g.setCustomCardAmountSymbol("￥");
    g.setCustomCardName(i + " Test email I am is is is my my my my buzzing buzzing buzzing buzzing asking asking asking Microsoft Microsoft Microsoft Microsoft Microsoft Microsoft");
    g.setCustomCardId("cardId_" + i);
    g.setCustomCardDesc("Test email I am is is is my my my my buzzing buzzing buzzing buzzing asking asking asking Microsoft Microsoft Microsoft Microsoft Microsoft Microsoft");
    g.setCustomCardThumbnail("https://hk.sobot.com/auth/_next/static/media/sideZh.74024132.png");
    if (i == 0) {
        List<SobotChatCustomMenu> menus2 = new ArrayList<>();
        menus2.add(m);
        g.setCustomMenus(menus2);
    } else if (i == 1) {
        List<SobotChatCustomMenu> menus2 = new ArrayList<>();
        menus2.add(m);
        menus2.add(mm);
        g.setCustomMenus(menus2);
    } else {
        List<SobotChatCustomMenu> menus2 = new ArrayList<>();
        menus2.add(m);
        menus2.add(mm);
        menus2.add(mmm);
        g.setCustomMenus(menus2);
    }
    goods.add(g);
}
customCard.setCustomCards(goods);

//Set card
info.setCustomCard(customCarddange);
```

##### ● Message Ticket Related

###### 1. Workbench Setup Message Interface

You can set up the message interface on the workbench.

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-3-1.png)

###### 2. Custom Configuration Of User Information On The Message Page

The validation and display logic for the three params of email, phone, and attachment in the message can be configured on the PC console page.

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-3-2.png)

###### 3. Jump To The Message Page

```js
/**
 * Jump to the message leaving interface
 *
 * @param context   Context Required
 * @param info     User's appkey Required. If the user is a platform user, pass the headquarter's appkey
 * @param isOnlyShowTicket true shows only the message record interface, false shows both the leave-a-message and message record interfaces
 */
ZCSobotApi.openLeave(Context context,Information info,boolean isOnlyShowTicket);
```

Example code:

```js
Information info = new Information();
info.setApp_key(et_appkey.getText().toString());/* Required */
//ticket skill group 
info.setLeaveMsgGroupId("6576d173af904d97b1d5d01a11cc66f5");
Map<String,String> map=new HashMap<>();
//Custom fields, key corresponds to the ID of the field added by the backend
map.put("834b34870b2e47daa1904d8f63ee55c2","zzz");
info.setLeaveCusFieldMap(map);
//Specify the message template ID to jump to a specific message interface
info.setLeaveTemplateId("7800560a37784ce1be064915c8389d28");
ZCSobotApi.openLeave(SobotStartActivity.this, info, false);
```

###### 4. Message Page Event Interception

SDK allows messages to redirect to a custom page. If you have this requirement, you can use the following method to set it up:

```js
ZCSobotApi.setSobotLeaveMsgListener(new SobotLeaveMsgListener() {
    @Override
    public void onLeaveMsg() {
      ToastUtil.showToast(getApplicationContext(),"Implement the method here, navigate to the page");
   }
});
```

###### 5. The Reply Button On The Message Details Interface In The Completed Status Can Be Configured To Show Or Hide Through The Param Setting.

```js
// For completed status messages, can users continue to reply? True means they can continue, false means they cannot.
// Default is true, users can always continue to reply.
ZCSobotApi.setSwitchMarkStatus(MarkConfig.LEAVE_COMPLETE_CAN_REPLY, true);
```

###### 6. Get Message Replies

```js
/**
 * Get the list of unread message replies. If there are unread replies, display the latest one in the notification bar. Click the notification to go to the message details page.
 *
 * If you use a method like scheduled tasks to get the latest message replies in real time, the interval between two requests (time) must be greater than 60 seconds for the API to return data.
 *
 * @param context Context Required
 * @param partnerId User's unique identifier, consistent with the partnerid passed in information
 * @param noReadLeaveReplyListener Callback for getting the list of unread message replies, SobotLeaveReplyModel: Single message reply object
 */
ZCSobotApi.getLastLeaveReplyMessage(SobotStartActivity.this,"your partnerid", new SobotNoReadLeaveReplyListener() {
        @Override
        public void onNoReadLeaveReplyListener(List<SobotLeaveReplyModel> sobotLeaveReplyModelList) {
            if(sobotLeaveReplyModelList!=null&&sobotLeaveReplyModelList.size()>0){
            // Send message reply notification. After clicking the notification, go to the message details page.
            ZCSobotApi.sendLeaveReplyNotification(SobotStartActivity.this, sobotLeaveReplyModelList.get(0), R.drawable.sobot_logo_small_icon, R.drawable.sobot_logo_small_icon);
            }
        }
});
```

###### 7. Add A Switch For Proactive Reminders Of Leaving Comments And Reviews

```js
// Completed message details page - Not evaluated: Whether to pop up the service evaluation window when returning (It will only pop up the first time, and will not pop up again on subsequent returns). Default is false (no popup).
info.setShowLeaveDetailBackEvaluate(true);
```

###### 8. Add A Comment Extension Param

```js
//Add leave message docking fields
List<SobotLeaveMsgFieldModel> leaveParamsExtends = new ArrayList<>();
//SobotLeaveMsgFieldModel property description: ID: Automatically generated ID by the docking field system; Value: Data to be passed; Params: Display field ID, such as city, address, corresponding to ID; Data is configured from the backend console.
leaveParamsExtends.add(new SobotLeaveMsgFieldModel("your id", "your value", "your params"));
info.setLeaveParamsExtends(leaveParamsExtends);

//Add leave message skill group
info.setLeaveMsgGroupId("your groupId");

//Add custom fields for leave messages. Key corresponds to the field ID added in the backend.
Map<String,String> map=new HashMap<>();
map.put("your field key","zzz");
info.setLeaveCusFieldMap(map);
```

##### ● Evaluation

###### 1. Set Up The Rating Interface

You can set it on the workbench, satisfaction evaluation interface:

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-4-1.png)

###### 2. Whether A Satisfaction Rating Pops Up When Clicking Back On The Left Side Of The Navigation Bar

Note: The satisfaction evaluation window can only pop up after the user has sent a message.

```js
// Whether to show a pop-up window when clicking back (Are you sure to end chat?)
info.setShowLeftBackPop(true);
// Whether to show satisfaction evaluation when clicking back on the left side of the navigation bar. True shows, false does not show; default is false
info.setShowSatisfaction(false);
```

![Image](https://img.sobot.com/mobile/sdk/new/images/v6/a-4-4-2.png)

###### 3. Whether The Close Button On The Right Side Of The Navigation Bar Is Displayed And Whether A Satisfaction Rating Pops Up When Clicked

Note: The satisfaction evaluation window can only pop up after the user has sent a message.

```js
// Set whether to show the close button on the right side of the navigation bar. True shows, false hides; default is false.
info.setShowCloseBtn(false);
// Set whether a satisfaction survey pops up when clicking the close button on the right side of the navigation bar. True pops up, false does not pop up; default is false.
info.setShowCloseSatisfaction(false);
```

###### 4. Configure The System To Release The Chat After The User Submits A Manual Satisfaction Rating

```js
/**
 * Configure to release chat after user submits manual satisfaction rating
 * @param context Context object
 * @param flag true means release chat false means do not release chat
 */
ZCSobotApi.setEvaluationCompletedExit(context,flag);
```

###### 5. When Returning From The Top Left Corner And Closing From The Top Right Corner, Whether To Display The "Not Evaluate For Now" Button In The Manual Satisfaction Evaluation Pop-up Interface Configuration

```js
/**
 * Top-left return and top-right close. When returning to the evaluation pop-up window, whether to show the "Not Evaluate For Now" button. Default is false (not shown).
 */
info.setCanBackWithNotEvaluation(true);
```

##### ● Message Related

###### 1. Send Text Messages

If your APP needs to actively send text messages to the agent, please use the following code:

```js
/**
 * Send text-based messages
 * @param context
 * @param content Text content
 */
ZCSobotApi.sendTextToUser(Context context,String content)
```

###### 2. Set Whether To Enable Message Notifications

When the user is not on the chat interface and receives a message from the agent, the app can show a reminder in the notification bar. Clicking the notification bar reminder will redirect to the chat interface.

```js
/**
* Set whether to enable message notifications. Default is no notification.
* @param context
* @param flag
* @param smallIcon The ID of the small icon. Set the small image in the notification bar. The size is generally recommended to be 24x24.
* @param largeIcon The ID of the large icon.
*/
public static void setNotificationFlag(Context context, boolean flag, int smallIcon, int largeIcon);
```

Example code:

```js
// Set whether to enable message notifications
ZCSobotApi.setNotificationFlag(getApplicationContext(), true, R.drawable.sobot_logo_small_icon, R.drawable.sobot_logo_icon);
```

###### 3. Set Up Offline Messages

Enable offline messages:

```js
// Enable the channel to accept offline messages. After enabling, messages will be sent in broadcast form. If this function is not needed, you can skip the call.
ZCSobotApi.checkIMConnected(getApplicationContext(), "uid");
```

Close offline messages:

```js
// Close the channel and clear the current chat cache
ZCSobotApi.closeIMConnection(getApplicationContext());
```

###### 4. Get The Number Of Unread Messages

Without entering the SDK page, get the number of unread messages.

```
/**
     * Get the number of unread messages
     * @param context Context Required
     * @param appkey User's appkey Required If the user is a platform user, pass the headquarter's appkey
     * @param partnerid User's unique identifier. Do not pass the same value.
     * @param callBack Return content is NureadMsgModel object. Field descriptions: offlineSize - Number of offline messages, unAckSize - Number of unconfirmed messages, unReadSize - Number of locally recorded unread messages. Entering the SDK page will clear this data.
     */
ZCSobotApi.offlineMsgSize(this,"your appkey", "your partnerid", new StringResultCallBack<NureadMsgModel>() {

                @Override
                public void onSuccess(NureadMsgModel nureadMsgModel) {                    
                    StringBuilder builder = new StringBuilder();
                    builder.append("Number of unread messages: ").append(nureadMsgModel.getUnReadSize()).append(" messages\n");
                    builder.append("Number of offline messages: ").append(nureadMsgModel.getOfflineSize()).append(" messages\n");
                    builder.append("Number of unconfirmed messages: ").append(nureadMsgModel.getUnAckSize()).append(" messages\n");
                    builder.append("Total number of unread messages: ").append((nureadMsgModel.getUnReadSize()+nureadMsgModel.getOfflineSize())+nureadMsgModel.getUnAckSize()).append(" messages\n");
                    Toast.makeText(SobotStartActivity.this, builder.toString(), Toast.LENGTH_SHORT).show();
                }

                @Override
                public void onFailure(Exception e, String des) {
                    if(SobotStringUtils.isNoEmpty(des)) {
                        Toast.makeText(SobotStartActivity.this, des, Toast.LENGTH_SHORT).show();
                    }
                }
            });
```

###### 5. Register Broadcast, Get Newly Received Messages

After registering the broadcast, you can get newly received messages when the message channel is connected.

1 Register Broadcast

```js
/**
* action:ZhiChiConstants.sobot_unreadCountBrocast
*/
IntentFilter filter = new IntentFilter();
filter.addAction(ZhiChiConstant.sobot_unreadCountBrocast);
contex.registerReceiver(receiver, filter);
```

2 Receive new information

Receive information in the onReceive method of BroadcastReceiver.

```js
public class MyReceiver extends BroadcastReceiver {
  @Override
  public void onReceive(Context context, Intent intent) {
    // New message content
    String content = intent.getStringExtra("content");
    Bundle bundle = intent.getExtras();
    ZhiChiPushMessage message = (ZhiChiPushMessage) bundle.get("sobotMessage");
    LogUtils.i("   New message content:" + content);
    LogUtils.i(" Message object:" + message.toString());
    unread_msg_num.setText(noReadNum + "");
  }
}
```

###### 6. Send Location Message

If your APP needs to send the customer's location information, please follow the steps below to set it up (note that map positioning needs to be developed by the developer).

1. The agent chat interface has a configuration for the send button (displayed in the menu panel when clicking the "+" button, shown only after trans-to-agent), the code is as follows:

```js
// Menu action When a button is clicked, the corresponding action will be returned to the callback as a basis,
// to determine which button the user clicked, and can be customized
final String ACTION_LOCATION = "sobot_action_location";
// Configure the location sending button
ChattingPanelUploadView.SobotPlusEntity locationEntity = new ChattingPanelUploadView.SobotPlusEntity(R.drawable.sobot_location_btn_selector, ResourceUtils.getResString(getApplicationContext(), "sobot_location"), ACTION_LOCATION);
List<ChattingPanelUploadView.SobotPlusEntity> tmpList = new ArrayList<>();
tmpList.add(locationEntity);
SobotUIConfig.pulsMenu.operatorMenus = tmpList;
```

2. Set the callback for the location send button:

```js
//sSobotPlusMenuListener can only have one, otherwise, the following will overwrite the previous one (for example: in the plus sign 
//if both custom add location and order button are added, you can determine which button is clicked based on the action and handle it accordingly)
SobotUIConfig.pulsMenu.sSobotPlusMenuListener = new SobotPlusMenuListener() {
    @Override
    public void onClick(View view, String action) {
        if (ACTION_LOCATION.equals(action)) {
            Context context = view.getContext();
            //After obtaining location information on the map positioning page, send it to the agent:
            SobotLocationModel locationData = new SobotLocationModel();
            //Map snapshot, must pass the local image address. Note: If not passed, a default map image will be displayed
            locationData.setSnapshot(Environment.getExternalStorageDirectory().getAbsolutePath()  +"/1.png");
            //Latitude
            locationData.setLat("40.057406655722");
            //Longitude
            locationData.setLng("116.2964407172");
            //Label name
            locationData.setLocalName("Jinma Building");
            //Label address
            locationData.setLocalLabel("Jinma Building, Liudaokou, Haidian District, Beijing");
            ZCSobotApi.sendLocation(context, locationData);
        }
    }
};
```

###### 6. Customize Click Events For Hyperlinks (Intercept Scope: Help Center, Messages, Chat, Message History, Product Card, Order Card, Location Card)

```js
// Link click event, determine whether to intercept based on the return result. If true is returned, intercept; if false, do not intercept.
// It can be an order number, product details address, etc. Customers can define custom rules for interception. When returning true, custom information will be returned.
// Interception scope (Help Center, Messages, Chat, Message Records, Product Cards, Order Cards)
ZCSobotApi.setNewHyperlinkListener(new NewHyperlinkListener() {
    @Override
    public boolean onUrlClick(String url) {
        // Example
        if (url.contains("baidu.com")) {
            ToastUtil.showToast(getApplicationContext(), "Clicked hyperlink, url=" + url);
            // If the URL link is Baidu, intercept
            // do().....
            return true;
        }
        // Example
        if (url.contains("Order Number: 123456789")) {
            ToastUtil.showToast(getApplicationContext(), "Clicked hyperlink, url=" + url);
            // If the link is an order card, intercept
            // do().....
            return true;
        }
        return false;
    }
    @Override
    public boolean onEmailClick(String email) {
        ToastUtil.showToast(getApplicationContext(), "Clicked Email, email=" + email);
        return false;
    }
    @Override
    public boolean onPhoneClick(String phone) {
        ToastUtil.showToast(getApplicationContext(), "Clicked phone, phone=" + phone);
        return false;
    }
});
```

Set the callback for the location card click event:

```js
// After clicking the location card, Baidu Map will be opened by default. If Baidu Map is not installed, then Amap will be opened. The click event of the location card can be intercepted for custom handling.
SobotOption.mapCardListener = new SobotMapCardListener() {
     @Override
     public boolean onClickMapCradMsg(Context context, SobotLocationModel locationModel) {
          if (context != null && locationModel != null) {
               ToastUtil.showCustomToast(context, "Intercepted location card click event");
               // Open Amap first
               // StMapOpenHelper.firstOpenGaodeMap(context, locationModel);
               // Open Baidu Map first
               // StMapOpenHelper.firstOpenBaiduMap(context, locationModel);
          }
       // Return true to intercept; return false to not intercept
       return true;
     }
};
```

###### 8. Listen For Changes In The Current Chat Mode

```js
ZCSobotApi.setChatStatusListener(new SobotChatStatusListener() {
    @Override
    public void onChatStatusListener(SobotChatStatusMode chatStatusMode) {
        switch (chatStatusMode) {
            case ZCServerConnectRobot:
                ToastUtil.showToast(getApplicationContext(), "Bot chat mode");
                break;
            case ZCServerConnectArtificial:
                ToastUtil.showToast(getApplicationContext(), "Trans-to-agent agent chat mode");
                break;
            case ZCServerConnectOffline:
                ToastUtil.showToast(getApplicationContext(), "Offline");
                break;
            case ZCServerConnectWaiting:
                ToastUtil.showToast(getApplicationContext(), "Waiting in queue for agent only");
                break;
        }
    }
});
```

###### 9. Regular Expression For Replacing Mobile Or Landline Numbers In Messages

```js
ZCSobotApi.replacePhoneNumberPattern(String regex);
```

###### 10. Replace The Regular Expression For Hyperlink Recognition In Messages

```js
ZCSobotApi.replaceWebUrlPattern(String regex);
```

###### 11. Hide The Time Prompt In The Message List

```js
//isHide true hides, false shows. Default is false.
ZCSobotApi.hideTimemsgForMessageList(Context context, boolean isHide);
```

#### Function Customization

##### ● UI Setting Instructions

In order to make the interface style of the agent window consistent with the overall APP that integrates the Sobot agent SDK, the Sobot agent SDK provides simple UI customization options.

###### 1. Configure Property Values

The following attributes can be set in the Application's oncreate() method:

```js
// Set whether the first button on the right side of the toolbar is displayed, default is displayed
SobotUIConfig.sobot_title_right_menu1_display = true;
// Set whether the second button on the right side of the toolbar is displayed, default is hidden (evaluation)
SobotUIConfig.sobot_title_right_menu2_display = true;
// Set whether the third button on the right side of the toolbar is displayed, default is hidden
SobotUIConfig.sobot_title_right_menu3_display = true;
// Modify the image of the third button on the right side of the toolbar (phone icon R.drawable.sobot_phone)
SobotUIConfig.sobot_title_right_menu3_bg = R.drawable.sobot_phone;
// Set the phone number that the third button on the right side of the toolbar needs to dial
SobotUIConfig.sobot_title_right_menu3_call_num = "18510000000";
```

###### 2. Control The Switch For Horizontal And Vertical Screen Display

```js
// true for landscape, false for portrait; default is false for portrait
ZCSobotApi.setSwitchMarkStatus(MarkConfig.LANDSCAPE_SCREEN, false);
```

###### 3. Whether To Turn On The Notch Screen Switch In Landscape Mode

```js
// Only works in landscape mode; portrait mode is already adapted, you can modify the status bar color
// true to turn on, false to turn off; default is false (off)
ZCSobotApi.setSwitchMarkStatus(MarkConfig.DISPLAY_INNOTCH, true);
```

###### 4. UI Style Replaced By Resource With The Same Name

In the customer APP, adding a color with the same name in colors.xml can override the color style in the Sobot SDK; you can also replace the image in the Sobot SDK interface by placing an image resource with the same name in the same location in the main project; similarly, you can replace the text in the Sobot SDK interface by placing a text resource with the same name in the same location in the main project.

The following are commonly used color configurations. You can find more colors and image resources by downloading the source code package in the manual integration module.

```js
<!-- Default theme color green -->
    <color name="sobot_color">@color/sobot_common_green</color>
    <color name="sobot_color_transparency_10">@color/sobot_common_green_transparency_10</color>

    <!-- Text color Primary text color Black text in most interfaces -->
    <color name="sobot_color_text_first">#161616</color>
    <!-- Text color Secondary text color -->
    <color name="sobot_color_text_second">#777474</color>
    <!-- Text color Placeholder text color -->
    <color name="sobot_color_text_third">#A3A5A8</color>
    <!-- General Background color -->
    <color name="sobot_color_common_bg">#F5F5F5</color>
    <!-- Background color Level one -->
    <color name="sobot_color_bg_first">#FFFFFF</color>
    <!-- Background color Level two Secondary black background (Popup bottom color, chat bottom operation bar, cell -->
    <color name="sobot_color_bg_second">#F5F5F5</color>
    <!-- Background color Level three Bubble containing other content's background color (Multi-round chat, product -->
    <color name="sobot_color_bg_third">#FFFFFF</color>
    <!-- Background color Chat page Bottom quick menu Input box area Extended menu -->
    <color name="sobot_color_bg_four">#FFFFFF</color>
    <!-- Line Button border color -->
    <color name="sobot_color_line_button_frame">#D9D9D9</color>
    <!-- Line Divider color -->
    <color name="sobot_color_line_divider">#EBEBEB</color>
    <!-- Line Divider color 2 -->
    <color name="sobot_color_line_divider_2">#F5F5F5</color>
    <!-- Header Start -->

    <!-- Header navigation bar and status bar default gradient background Left Start -->
    <color name="sobot_color_title_bar_left_bg">@color/sobot_color_bg_first</color>
    <!-- Header navigation bar and status bar default gradient background Right End -->
    <color name="sobot_color_title_bar_bg">@color/sobot_color_bg_first</color>
    <!-- Header nickname color -->
    <color name="sobot_color_title_bar_nike_name">@color/sobot_white</color>
    <!-- Header company name color -->
    <color name="sobot_color_title_bar_company_name">@color/sobot_white</color>
    <!-- Header side menu font color -->
    <color name="sobot_color_title_bar_menu_text">@color/sobot_white</color>

    <!-- Top no network message Background color -->
    <color name="sobot_no_net_bgcolor">#FFF1F0</color>

    <!-- Announcement layout background color -->
    <color name="sobot_announcement_bgcolor">#FFFBE6</color>
    <!-- Announcement title font color -->
    <color name="sobot_announcement_title_color">#161616</color>
    <!-- Announcement card Horizontal line color -->
    <color name="sobot_announcement_line_color">#1AFA8314</color>
    <!-- Non-top announcement hyperlink Text color -->
    <color name="sobot_announcement_link_color">@color/sobot_common_blue</color>

    <!-- Middle Chat list -->
    <!-- Chat background -->
    <color name="sobot_color_chat_bg">@color/sobot_color_bg_first</color>
    <!-- Text message bubble Left Black text -->
    <color name="sobot_left_msg_text_color">@color/sobot_color_text_first</color>
    <!-- Text message bubble Left Light gray text For descriptions -->
    <color name="sobot_left_msg_text_color_des">@color/sobot_color_text_third</color>
    <!-- Text message bubble Right White text -->
    <color name="sobot_right_msg_text_color">@color/sobot_white</color>
    <!-- Hyperlink color Left -->
    <color name="sobot_color_link">@color/sobot_common_blue</color>
    <!-- Hyperlink color Right -->
    <color name="sobot_color_rlink">@color/sobot_common_blue</color>
    <!-- Chat interface reminder font color -->
    <color name="sobot_color_remind_text">@color/sobot_color_text_third</color>
    <!-- Message reminder hyperlink color -->
    <color name="sobot_color_link_remind">@color/sobot_color</color>
    <!-- File message bubble color -->
    <color name="sobot_chat_file_bgColor">@color/sobot_color</color>
    <!-- Message bubble left background default color -->
    <color name="sobot_chat_left_bgColor">@color/sobot_color_bg_second</color>
    <!-- Message bubble right background default color Gradient Left Start -->
    <color name="sobot_chat_right_bgColor_start">@color/sobot_gradient_start</color>
    <!-- Message bubble right background default color Gradient Right End -->
    <color name="sobot_chat_right_bgColor_end">@color/sobot_gradient_end</color>
    <!-- Left message bubble nickname color -->
    <color name="sobot_chat_left_nikename_color">@color/sobot_color_text_third</color>
    <!-- Right message bubble nickname color -->
    <color name="sobot_chat_right_nikename_color">@color/sobot_color_text_third</color>
    <!-- Quoted message -->
    <!-- Text message bubble Left Quote type color Black text -->
    <color name="sobot_left_appoint_msg_type_color">@color/sobot_color_text_second</color>
    <!-- Text message bubble Left Quote content color Black text -->
    <color name="sobot_left_appoint_msg_text_color">@color/sobot_color_text_third</color>
    <!-- Text message bubble Left Quote card inside color Black text -->
    <color name="sobot_left_appoint_msg_card_text_color">@color/sobot_color_text_first</color>
    <!-- Text message bubble Right Quote type color White text -->
    <color name="sobot_right_appoint_msg_type_color">#E6FFFFFF</color>
    <!-- Text message bubble Right Quote content color White text -->
    <color name="sobot_right_appoint_msg_text_color">#D9FFFFFF</color>
    <!-- Message bubble right Line color -->
    <color name="sobot_chat_right_line">#99FFFFFF</color>
    <!-- Message bubble left Line color -->
    <color name="sobot_chat_left_line">#CCCCCC</color>
    <!-- Right quoted message Quote part background color -->
    <color name="sobot_chat_appoint_right_transparent_bg">#24FFFFFF</color>
    <!-- Left quoted message Quote part background color -->
    <color name="sobot_chat_appoint_left_transparent_bg">#FFFFFF</color>
    <!-- Quoted message Small block Placeholder background color -->
    <color name="sobot_chat_appoint_zhanwei_bg">#CDD9EA</color>
    <!-- Image control with preloading effect Background color -->
    <color name="sobot_color_progress_image_bg">#EBEBEB</color>

    <!-- Bottom -->
    <!-- Hold to record animation panel Background gradient -->
    <color name="sobot_color_chat_bottom_record_sound_bg_start">#00FFFFFF</color>
    <color name="sobot_color_chat_bottom_record_sound_bg_end">#FFFFFF</color>
    <!-- Background color Chat page Bottom quick menu Input box area Extended menu -->
    <color name="sobot_color_chat_bottom_bg">@color/sobot_color_bg_four</color>
    <!-- Custom label border color -->
    <color name="sobot_lable_stroke_color">@color/sobot_color_line_divider</color>
    <!-- Custom label default fill color -->
    <color name="sobot_lable_nomal_bg_color">@color/sobot_color_chat_bottom_bg</color>
    <!-- Custom label font color -->
    <color name="sobot_lable_text_color">@color/sobot_color_text_first</color>

    <!-- Message input box Text color -->
    <color name="sobot_color_bottom_msg_input_color">@color/sobot_color_text_first</color>

    <!-- After clicking the plus Panel background -->
    <color name="sobot_color_bottom_bg">@color/sobot_white</color>
    <!-- After clicking the plus Panel background Button font color -->
    <color name="sobot_color_bottom_btn_wz_color">@color/sobot_color_text_first</color>

    <!-- Prompt popup Button text color -->
    <color name="sobot_color_dialog_btn_content_color">@color/sobot_common_blue</color>

    <!-- Leave a message related -->
    <!-- Leave a message Navigation bar switch Text underline color -->
    <color name="sobot_postMsg_nav_indicator_color">@color/sobot_white</color>
    <!-- Leave a message Navigation bar switch Selected font color -->
    <color name="sobot_postMsg_nav_sel_tx_color">@color/sobot_white</color>
    <!-- Leave a message Navigation bar switch Unselected font color -->
    <color name="sobot_postMsg_nav_tx_color">@color/sobot_white</color>
    <!-- Leave a message Guide hyperlink color -->
    <color name="sobot_postMsg_url_color">@color/sobot_common_blue</color>
    <!-- Leave a message Upload image Popup option background color -->
    <color name="sobot_color_setting_item_pressed">@color/sobot_color_white</color>

    <!-- Chat interface button background color -->
    <color name="sobot_btn_bg">@color/sobot_color</color>
    <color name="sobot_btn_bg_pressed">@color/sobot_color</color>
    <color name="sobot_btn_bg_disable">#EFF3FA</color>
    <color name="sobot_text_btn_color">#ffffff</color>
    <color name="sobot_text_btn_color_pressed">#80ffffff</color>

    <!-- Delete history message font color -->
    <color name="sobot_text_delete_hismsg_color">@color/sobot_common_red</color>
    <!-- Toast background color -->
    <color name="sobot_color_toast_bg">#BF000000</color>

    <!-- Product information title color -->
    <color name="sobot_goods_title_text_color">@color/sobot_color_text_first</color>
    <!-- Product information description color -->
    <color name="sobot_goods_des_text_color">@color/sobot_color_text_second</color>
    <!-- Product price color -->
    <color name="sobot_goods_price_text_color">@color/sobot_color</color>

    <!-- Order card General text color -->
    <color name="sobot_order_label_text_color">@color/sobot_color_text_first</color>
    <!-- Order card Order status color -->
    <color name="sobot_order_status_text_color">#E67F17</color>
    <!-- Order card Product description color -->
    <color name="sobot_order_des_text_color">@color/sobot_color_text_third</color>

    <!-- Leave a message record details Time line color -->
    <color name="sobot_ticket_deal_line_grey">@color/sobot_color_line_divider</color>
    <!-- Leave a message Select business Font color -->
    <color name="sobot_post_msg_template_text_color">@color/sobot_color</color>

    <!-- Evaluation, skill group, switch business, leave a message popup Selection button selected background color -->
    <color name="sobot_dialog_btn_select">@color/sobot_color</color>

    <!-- Evaluation Dislike reason card Label button default text color -->
    <color name="sobot_chat_lable_checkbox_text_color">@color/sobot_color_text_first</color>
    <!-- Evaluation Submit button -->
    <color name="sobot_evaluate_btn_press">@color/sobot_color</color>
    <color name="sobot_evaluate_btn_nor">#4ADABE</color>

    <!-- Ten-point evaluation (Block) Selected color -->
    <color name="sobot_ten_evaluate_select">#FA8314</color>
    <!-- Five-star rating widget Corresponding description color -->
    <color name="sobot_color_evaluate_ratingBar_des_tv">#FA8314</color>

    <!-- Multi-round chat Label font color -->
    <color name="sobot_template2_lable_text_color">@color/sobot_color</color>
    <!-- Multi-round chat View details font color -->
    <color name="sobot_template4_more_text_color">@color/sobot_common_blue</color>

    <!-- History record Guided question Problem color -->
    <color name="sobot_color_suggestion_history">@color/sobot_color_text_first</color>
    <!-- File message Send and download Button background -->
    <color name="sobot_btn_normal_color">@color/sobot_color</color>

    <!-- File progress bar foreground color -->
    <color name="sobot_sectorProgressView_fgColor">#4D000000</color>
    <!-- Semi-transparent -->
    <color name="sobot_half_transparent">#73000000</color>

    <!-- Auto-complete background color -->
    <color name="sobot_auto_complete_press">@color/sobot_color_bg_second</color>
    <color name="sobot_auto_complete">@color/sobot_color_transparent</color>

    <!-- Custom card -->
    <color name="sobot_card_goods_desc">@color/sobot_color_text_third</color>
    <color name="sobot_card_goods_price">#FFFE7F02</color>
    <!-- Border -->
    <color name="sobot_card_mgs_bg">@color/sobot_white</color>
    <color name="sobot_card_mgs_bg1">#fffdff</color>
    <color name="sobot_card_mgs_bg2">#fbf8fb</color>
    <color name="sobot_card_mgs_bg3">#f4f1f5</color>
    <!-- Unread guide -->
    <color name="sobot_readinfo_bg">@color/sobot_color_bg_third</color>
    <!-- Ticket resolved status -->
    <color name="sobot_ticket_resolved_text">#52C41A</color>
    <color name="sobot_ticket_resolved_bg">#F2FFE6</color>
    <!-- Ticket processing status -->
    <color name="sobot_ticket_deal_text">#FA8314</color>
    <color name="sobot_ticket_deal_bg">#FFF5E3</color>
    <!-- Ticket awaiting reply status -->
    <color name="sobot_ticket_reply_text">#2D85EC</color>
    <color name="sobot_ticket_reply_bg">#E6F7FF</color>
    <!-- Rating level -->
    <color name="sobot_evaluate_text_unselect">#B6BECB</color>
    <color name="sobot_evaluate_text_select">@color/sobot_color_text_first</color>
    <!-- Light green Rating label button hollow background color -->
    <color name="sobot_light_green">#E6F6F7</color>
```

###### 5. Set Night (Dark) Mode

After upgrading the SDK to V7 (4.3.0), this function is implemented through the background visitor client settings, local method delete.

```js
/** Set the interface to day, night, or system-following mode. Default is system-following.
     * Set after SDK initialization because it resets after each initialization.
     * @param mode 0 / AppCompatDelegate.MODE_NIGHT_AUTO: Switch between day/night themes based on current time
     *                 1 / AppCompatDelegate.MODE_NIGHT_NO: Day mode
     *                 2 / AppCompatDelegate.MODE_NIGHT_YES: Night mode
     *                 Other / AppCompatDelegate.MODE_NIGHT_FOLLOW_SYSTEM: Follow system settings
     *            
     */
ZCSobotApi.setLocalNightMode(context, int mode);
```

##### ● Function Configuration Instructions

###### 1. Customize The Display Time Range For Chat History

If you want to set that users can only see chat records within xx days, then you can call the following method to make the setting:

```js
/**
 * Control the time range for displaying historical chat records. It can show messages within 60 days at most, in minutes.
 * If not passed, all historical records will be displayed by default.
 * @param time Query time (e.g., 100 - means chat records from 100 minutes ago)
 */
ZCSobotApi.setScope_time(context, time);
```

###### 2. "+" Sign Panel Menu Extension

In the agent chat interface, the menu panel that appears after clicking the "+" button can be customized to add menus as needed. The code is as follows:

```js
private void customMenu(){
    //Add extended menu data
    ArrayList<ChattingPanelUploadView.SobotPlusEntity> objects = new ArrayList<>();
    /**
     * SobotPlusEntity is a custom menu entity class
     * @param iconResId Menu icon drawableId
     * @param name      Menu name
     * @param action    Menu action When the button is clicked, the corresponding action will be returned to the callback
     *                  Use this as a basis to determine which button the user clicked
     */
     objects.add(new ChattingPanelUploadView.SobotPlusEntity(R.drawable.sobot_camera_picture_button_selector, "Location", "action_location"));
     objects.add(new ChattingPanelUploadView.SobotPlusEntity(R.drawable.sobot_camera_picture_button_selector, "Check-in", "action_sing_in"));
     objects.add(new ChattingPanelUploadView.SobotPlusEntity(R.drawable.sobot_camera_picture_button_selector, "Favorite", "action_ollection"));
     //Add data in both bot mode and human mode
     //SobotUIConfig.pulsMenu.menus = objects;
     //Add data only in human mode
     SobotUIConfig.pulsMenu.operatorMenus = objects;
     //Set callback
      SobotUIConfig.pulsMenu.sSobotPlusMenuListener = new SobotPlusMenuListener() {
         @Override
         public void onClick(View view, String action) {
            //action corresponds to the action in the entity class
            ToastUtil.showToast(getApplicationContext(), "action:"+action);
         }
      };
}
```

###### 3. Sobot Log Display Switch

```js
/**
* true shows log information, default false does not show
*/
ZCSobotApi.setShowDebug(false);
```

###### 4. Multilingual Support

Method 1:  
Currently, the SDK supports multiple languages such as English and Chinese. The language will automatically switch and adapt based on the current phone language. If the current phone language is not recognized, Chinese will be used by default.

To add a new language package, put the supported language file into the corresponding language directory. For example: English path: sobotsdk/src/main/res/values-en/strings.xml.

Description: The language folder name is values- followed by the language identifier, such as values-en; the name of strings.xml remains unchanged.

Method Two,

[《Customer SDK Supported Language Code Table》](https://shimo.im/sheets/47kgMzwgpOCrjD3V/MODOC)

```js
/**
 * Specify the use of international language package
 * @param language Specify language code, for example: "zh-Hans": Simplified Chinese, "en": English, refer to "Customer SDK Supported Language Code Table" for other language codes
 * @param isUse Whether to use the specified language
 */
ZCSobotApi.setInternationalLanguage(context,language, isUse);
```

Special Handling:  
If manual evaluation or bot evaluation tags are configured in multilingual scenarios, multilingual display is not supported. You can hide the display through the following attributes (this does not affect the use of the evaluation function, only the tags are missing in the evaluation content).

```js
//  Hide bot evaluation labels. Default is not hidden. True hides; false shows
info.setHideRototEvaluationLabels(false);

//  Hide manual evaluation labels. Default is not hidden. True hides; false shows
info.setHideManualEvaluationLabels(false);
```

###### 5. Sobot Partial Feature Page Back Click Monitoring (Only Records Without Interception), You Can Add Your Own Logic (E.g., Tracking)

```js
ZCSobotApi.setFunctionClickListener(new SobotFunctionClickListener() {
   @Override
   public void onClickFunction(Context context, SobotFunctionType functionType) {
       //1: Leave a message return, 2: Chat page return, 3: Help center return, 5: Call the agent 
       LogUtils.i(functionType.toString());
   }
});
```

###### 6. Security Check

1. Function Location: Online Channel Settings - Channel Security Settings - Security Key Settings - Check "Effective Scope (APP)".

2. After enabling the APP "Security Key" function, the SDK channel must pass the partnerid parameter. When integrating, add parameters "sign" and "createTime". Here, sign = "MD5(app_key + partnerid + secret + createTime)", createTime is a Unix millisecond timestamp; secret is a 32-character string, and createTime is in milliseconds.

3. After passing in the param, Sobot will decrypt the sign and verify whether the passed-in partnerid matches the partnerid in the sign. If they match, the system will connect to Sobot normally. If they do not match, the connection will fail. If the customer does not pass in the partnerid or sign, they will be considered an illegal user, and the connection will fail.

4. The function of "Security Key" in the APP, including enabling and disabling, takes effect in real time.

```js
//Pass the following two params when launching the Sobot page
//Signature
info.setSign(your sign);
//Timestamp in milliseconds
info.setCreateTime(create_time);
```

##### ● Information Class Description

###### 1. ID Related

| param  | Type | Required | Description | 
|:----|:----|:----|:----|
| app_key | String   | Yes | Must be set, initialization will fail if not set |  
| choose_adminid | String | No | Specifies agent ID |  
| tranReceptionistFlag | Integer | No | Specifies agent transfer type, 0 can transfer to other agents; 1 must transfer to the specified agent |  
| partnerid      | String | No  | Unique user identifier |
| robot_code     | String  | No | Bot ID for integration |  
| robot_alias    | String  | No | Alias corresponding to the bot ID |  
| faqId          | String  | No | FAQ parameter   |  
| sign           | String  | No | MD5 encrypted signature (app_key+partnerid+secret+create_time) |
| createTime     | String  | No | Timestamp |

###### 2. Agent Workbench Display

| param  | Type | Required | Description | 
|:----|:----|:----|:----|
| user_nick       | String  | No  | Nickname                |  
| user_name       | String  | No  | Real name            |  
| user_tels       | String  | No  | User phone number            |  
| user_emails     | String  | No   | User email            |  
| qq              | String  | No  | QQ                  |  
| remark          | String  | No  | Remark                |  
| face            | String  | No  | User-defined avatar      |  
| visit_title     | String  | No  | Title of the source page    |  
| visit_url       | String  | No  | Source URL       |  
| params          | String  | No  | User information            |  
| customer_fields | String  | No  | Custom fields with fixed keys |  
| group_name      | String  | No | Skill group name          |  
| groupid         | String  | No  | Skill group ID          |  
| isVip           | String  | No  | Whether the customer is VIP          |  
| vip_level       | String  | No  | VIP level          |  
| user_label      | String  | No  | User label          |

###### 3. Chat Page Related

| param  | Type | Required | Description | 
|:----|:----|:----|:----|
| service_mode     | Integer | No  | Custom access mode 1 Only bot , 2 Manual only , 3 Intelligent agent - bot first , 4 Intelligent agent - agent first  |

###### 4. Others

| param  | Type | Required | Description |
|:----|:----|:----|:----|
| transferaction            | String | No  | trans-to-agent Specifies skill group overflow                                       |
| summary_params            | String | No | trans-to-agent Custom field                                             |
| multi_params              | String | No  | Multi-round chat custom field                                          |
| margs                     | String | No | Extended field for hotspot guidance questions                                       |
| content                   | String | No  | Automatically sends product order information content                                     |
| queue_first               | Boolean | No | Specifies customer priority                                                 |
| isUseVoice                | Boolean | No | Whether to use voice function. Default is true, voice function can be used                  |
| isUseRobotVoice           | Boolean | No | Whether to use bot voice function. Default is false, bot cannot use voice function and will convert to text |
| isShowLeftBackPop         | Boolean | No | Whether a pop-up appears when returning from the top-left corner (e.g., "Would you like to end the chat?"). Default is false, no pop-up |
| isShowSatisfaction        | Boolean | No | Whether a satisfaction survey pops up when clicking the back button in the navigation bar. Default is false, pop-up appears if false   |
| isShowCloseSatisfaction   | Boolean | No | Whether a satisfaction survey pops up when closing the navigation bar. Default is false, pop-up appears if false. |
| equipmentId               | String  | No | Equipment ID                                                     |
| tranReceptionistFlag      | Integer| No  | Transfer type (0 - Can transfer to other agents, 1 - Must transfer to a specified agent)               |
| transferKeyWord           | HashSet | No | trans-to-agent Keywords                                                 |
| isCloseInquiryForm        | Boolean | No | Whether to close pre-query form                                                  |
| leaveMsgGuideContent      | String | No | Leave message guidance copy                                                 |
| leaveMsgGroupId           | String | No | Leave message skill group                                               |
| leaveCusFieldMap          | Map   | No  | Leave message custom fields                                             |
| leaveParamsExtends        | List  | No   | Integration fields                                             |
| leaveTemplateId           | List  | No   | Leave message template ID                                             |
| hideMenuSatisfaction      | Boolean | No | Hide evaluation                                                 |
| hideMenuLeave             | Boolean | No | Hide leave message                                               |
| hideMenuPicture           | Boolean | No | Hide picture                                                |
| hideMenuVedio             | Boolean | No | Hide video                                               |
| hideMenuCamera            | Boolean | No | Hide camera                                                 |
| hideMenuFile              | Boolean | No | Hide file                                               |
| showLeaveDetailBackEvaluate        | Boolean | No | Pop up service evaluation window when returning from the leave message detail interface                                               |
| canBackWithNotEvaluation        | Boolean | No | Temporarily not evaluate button when the evaluation window pops up                                               |
| hideRototEvaluationLabels        | Boolean | No| Whether to hide bot evaluation labels                                               |
| hideManualEvaluationLabels        | Boolean | No | Whether to hide manual evaluation labels                                               |
| locale                    | String | No | Server API internationalization language                                              |
| helpCenterTel             | String | No | Help center adds a call phone number                                              |
| helpCenterTelTitle        | String | No | Help center phone number button field                                              |
| hideMenuManualLeave       | Boolean | No | Only hides leave message under manual status                                             |
| isShowRightMsgFace       | Boolean | No | Whether to display avatar on the right-side messages                                             |
| isShowRightMsgNickName       | Boolean | No | Whether to display nickname on the right-side messages                                             |
| isShowEveryLeftMsgFaceNickName       | Boolean | No | Whether to display nickname and avatar on every left-side message                                             |

#### Source Code And Demo

[Click to download Demo source code](https://github.com/ZCSDK/Sobot_Sdk_Demo_Android_v6_kt);

[Click to download the installation package](https://img.sobot.com/mobile/sdk/sobot_sdk_demo_android_v6.apk);

[Click to view Demo usage tutorial](https://img.sobot.com/mobile/sdk/sobot_sdk_demo_android.mp4).

#### Update Notes

[<<SDK Version Update Notes>>](https://shimo.im/docs/ZzkLVP1x4wS2Qo3Q)

#### Sobot SDK Compliance Configuration Guide

Please refer to: [<<Sobot SDK Compliance Configuration Guide>>](https://www.zhichi.com/docs/sdk/sdk_compliance_configuration_guide.html)

Please inform users about the use of the Sobot agent SDK in the "Privacy Policy". Refer to the following terms:

```js
SDK Name: Sobot agent SDK

Service Type: agent system

Types of Personal Information Collected: Device and system information (including operating system type, system version, APP package name, APP version, device type, device manufacturer, device model, network type), sensors (including accelerometer and proximity sensor), network identity information (IP address)

Privacy Policy Link: https://www.zhichi.com/docs/clause/sdk-clause.html
```