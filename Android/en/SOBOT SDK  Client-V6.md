[SDK Name]: Zhizhi Technology SDK Visitor Client  

[Developer]: Beijing Zhizhi Bochuang Technology Co., Ltd

[Company Name]: Beijing Sobot Innovation Technology Co., Ltd. 

[Package Name]: com.sobot.chat

[Personal Information Processing Rules]: [Privacy Policy](https://www.zhichi.com/docs/clause/sdk-clause.html)

[Compliance Description]: [Compliance Description](https://www.zhichi.com/docs/sdk/sdk_compliance_configuration_guide.html)

[Main Functions]: The ZhiChi Technology SDK visitor terminal provides enterprises with a comprehensive set of intelligent customer service solutions. The ZhiChi customer service SDK includes both customer service business logic and interactive interfaces; enterprises can integrate ZhiChi customer service into their APPs in just two simple steps, enabling the APPs to provide 7*24-hour customer service.


Source code download link: [Android_SDK_X_4.2.8](https://img.sobot.com/mobile/sdk/Android_SDK_X_4.2.8.zip)

Dependency: 'com.sobot.chat:sobotsdk_x:4.2.8.2'


[Note]

If your application is submitted to the Google Play Store and encounters issues during review, the developer must remove the permissions [READ_MEDIA_IMAGES] and [READ_MEDIA_VIDEO] from the application manifest, and use system photo selectors such as the Android photo picker.

Please use the Google version corresponding to the Zhizhi Customer Service SDK: [[Latest version address]](https://central.sonatype.com/artifact/com.sobot.chat/sobotsdk_g)


Dependency: 'com.sobot.chat:sobotsdk_g:+'


Update Description SDK-4.2.8.2 (2025-09-04)

[Optimization] Modify the obfuscation and packaging method to avoid conflicts with other third-party SDKs


Update Notes SDK-4.2.8.1 (2025-08-29)

[New] Large model robot: Semantic conversation termination & transfer to designated group for human assistance

[New] Switch Robot option displays the current selected state

[Optimization] Optimize the logic of permission prompts in landscape mode and enable direct sending after the keyboard pops up

[Optimization] Change the way users click to play videos to online video playback

[Optimization] Android Webview page supports uploading attachments for work orders

[Optimization] Fix UI issues with product cards


Update Description SDK-4.2.7.1 (2025-07-28)

[New] Large model robot answers trigger sensitive words to display corresponding prompts


Update Notes SDK-4.2.6 (2025-07-08)

[Optimization] Trigger logic for transitioning from large model robot to human assistance


Update Description SDK-4.2.5 (2025-07-02)

[New] Adapt to the interface of large model robots to send videos, images, and files

[New] Large model robots support displaying prompts for switching to human assistance

[New] Android 15 supports so library files with a page size of 16 KB

[New] Display attachments in work order details

[New] Work order satisfaction evaluation supports multiple languages

[Optimization] Multi-round message card adaptation

[Optimization] Fix the issue of duplicate display of custom cards

[Optimization] Fixed the issue where the background color of the navigation bar was incorrect when entering the customer service center for the first time

[Optimization] Fixed an issue where avatars were not displayed when returning and re-entering the system during delayed transfer to manual queue in manual mode only

[Optimization] Remove ssid/bssid support to comply with national SDK platform standards

[Optimization] 8.0 System selection of videos and files


Update description SDK-4.2.4 (2025-04-15)

[New] Large model robots support clicking and liking

[New] Add message card for large model robots

[New] Large model robot supports satisfaction evaluation

[New] Add button message type for large model robots

[New] Add human intervention strategy


Update Notes SDK-4.2.3 (2025-03-13)

[New] UI interface revision


Update Description SDK-4.2.2 (2025-01-09)

[New] Level 2 Satisfaction Evaluation

[New] Pre-inquiry form

[New] Large model robot supports displaying Markdown format data in answers


Update Notes for SDK 4.2.1 [2024-12-20]

[New] Customizable status for adaptation work orders

[New] Add custom fields when creating work orders from cards

[Optimization] Display style when hyperlink conversion to card fails


SDK 4.2.0 version update description [2024-11-01] #

[New] Support for large model robots

[New] Multi-language dynamic configuration and switching

[New] Added timezoneId and countryName fields to the initialization interface

[New] Dynamic configuration of navigation bar and phone support in the Help Center

[Optimization] Optimize the issue of mutual kicking in special scenarios when opening new windows

[Optimization] Foldable screen camera orientation

[Optimization] Remove the permission to read media audio (android.permission.READ_MEDIA_AUDIO)


Update Notes SDK-4.1.9 (2024-09-12)

[New] Compatibility with Android 15

[Optimization] Navigation adaptation

[Optimization] Overall solution for shortcut menu image development

[Optimization] Video download

[Optimization] Full-screen display of customer service center videos

[Optimization] Judgment of audio permission


Update Notes SDK-4.1.8 (2024-07-16)

[New] New message reminder

[New] Add a date and time combination field for comments

[New] Add phone number area code in the message

[New] Add semantic transfer to human


Update Notes SDK-4.1.7 (2024-06-24)

[New] Feedback prompt for image saving

[New] Quick menu hyperlinks can concatenate parameters

[New] Shortcut menu supports customizable icons

[New] New messages are displayed at the top of the message list by default

[New] Unread message guidance on the visitor's side of the seat


Update Description SDK-4.1.6 (2024-05-28)

[New] Adjustment of the UI for the permission usage prompt box when applying for permissions

[Optimization] Adapt "Select Pictures and Videos" Permissions to Android 14


Update description SDK-4.1.5 (2024-05-14)

[New] Add a custom field for selecting regions in message input

[Optimization] The issue of combining two video answers into one in the knowledge base


Update Description SDK-4.1.4.1 (2024-04-25)

[Optimization] Adapt "Select Pictures and Videos" permissions to Android 14


Update Notes SDK-4.1.4 (2024-04-23)

[New] Added a transfer to human service node in Duolun session

[New] Add a night mode switch

[New] Reasons for clicking and downvoting

[New] Universal card support for automatic sending by the system and automatic sending by customers

[Optimization] The image framework Glide v4 is compatible with versions 4.9.0 and above by default


Update Notes SDK-4.1.3 (2024-03-19)

[New] Support for setting prompts for transferring to human service

[New] Picasso image library supports versions v2.71828 and above

[Optimization] Custom card adaptation optimization


Update Notes SDK-4.1.2 (2024-02-02)

[New] Multi-round template style 1 supports multi-line display

[New] The newly created message page supports options for whether to display the problem description and whether the problem description is required

[Optimization] Multiple upload of message images

[Optimization] Optimization of satisfaction display

[Optimization] Some phones experience stuttering when playing videos


Update Notes SDK-4.1.1 (2023-12-22)

[New] Support for message quotation function

[New] Support for marking messages as read or unread


Update Notes SDK-4.0.9 (2023-11-02)

[Optimization] Traditional Chinese translation is inaccurate

[Optimization] Support for repeated invitation of customer service for evaluation


Update Notes SDK-4.0.8.1 (2023-09-21)

[New] Satisfaction evaluation supports modifying button text, hiding input box, and adjusting guidance text

[New] Malay


Update Description SDK-4.0.7 (2023-08-30)

[New] Add a default unchecked state for evaluations

[New] Deferred transfer to human service

[New] When the evaluation score is displayed as 10, the score value is displayed in 2 lines

[Optimization] Display menu inside the plus sign


Update Description SDK-4.06 (2023-07-17)

[Optimization] Unify the universal card coding, changing from 20 to 21


Update Notes SDK-4.0.5.1 (2023-07-06)

[New] Send custom cards

[New] Multiple rounds of collecting nodes now support resubmission after cancellation

[New] UI revision of message record list page

[New] The robot supports sending pictures, files, and videos

[Optimization] Fix the issue of incorrect font size on the problem details page of the customer service center


Update Notes SDK-4.0.4 (2023-06-01)

[New] Adapt to multi-language display

[Optimization] When sending videos on OPPO phones, it displays an error message saying the photo album cannot be opened

[Optimization] Announcement to prevent consecutive double clicks

[Optimization] Hot issue list and change overlap

[Optimization] When the evaluation is set to display 0 points by default, the submit button does not appear after selecting the first star


Update Notes SDK-4.0.3 (2023-04-06)

[New] Order cards support custom fields

[New] Voice-to-Text

[Optimization] The configuration methods in ZCSobotApi all need to be called after initialization to take effect

[Optimization] Change the close button in the top right corner to an image button


Update Notes SDK-4.0.1 (2022-12-08)

[New] Multiple rounds of answers support multiple messages

[Optimization] webview supports uploading video files


Update Description SDK-4.0.0 (2022-11-03)

[New] Upgrade SDK to adapt to V6 account functionality

[New] Support the personalized experience for thousands of users on the backend visitor side

[New] Support for configuring multi-action shortcut menus

[New] Support for new version FAQs






