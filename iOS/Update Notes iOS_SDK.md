Sobot_iOS_SDK_V7：


Standard Edition:[Sobot iOS_SDK_V7_4.3.0](https://github.com/ZCSDK/doc/blob/master/iOS/iOS_SDK.md). 


## Update Notes SDK-4.3.0 (2025-11-07)

1. [New] SDK upgrade V7 version supports background guest side upgrade to the new version

2. [Added] Upgrade the new UI

3. [Added] Artificial welcome language supports mixed display of images and texts

4. [New] Added table format recognition

5. [New] Support asynchronous reception mode and real-time reception mode

6. [Added] Customer service center supports customer groups with different conditions to achieve thousands of people

7. [New] Added a local configuration parameter for turning off the left swipe gesture

8. [New] Hot questions support guide words and group text configuration

9. [New] Refactoring message module implementation






Sobot_iOS_SDK_V6：

Standard Edition:[[iOS_SDK_v6]](https://img.sobot.com/mobile/sdk/iOS_SDK_4.2.8.zip)


##  Update Notes SDK-4.2.8 (2025-08-26)

1 [New] API to get the number of offline messages and unconfirmed messages

2 [Optimization] SDK switches robot options to display the current selected state

3 [New] Large model bot: semantically end the session and transfer the bot to the designated group



## Update Notes SDK-4.2.7 (2025-07-28)

1.[New]Large model robot answer triggers sensitive words and displays corresponding prompt language

2. [Optimization] Optimized the issue where there was no echo when closing the input box during message quoting.

## Update Notes SDK-4.2.6 (2025-07-07)

1.[New]Adapt large model robot interface to send videos, images, files

2.[New]Work Order Satisfaction Evaluation Adapts to Multilingual Management

3.[New]Modification of logic rules for clearing history records

4.[New]Show attachments in the message details header, switch to the new interface

5.[New]Large model robot click common issues and quick menu incoming rule modification

6.[New]Modification of Japanese text line break rules

7.[Optimization]Optimize multi-round card message adaptation

8.[Optimization]Optimize the processing rules for hyperlink recognition encoding

9. [Optimization] Optimize large model robot's failure to send when clicking on common issues.

10.[Optimization]Keyboard interaction adaptation for the new version of the pre-inquiry form in landscape mode

11. [Optimization] Large model robot error added new type handling

12. [Optimization] Large model robot directly answers historical record data parsing exception handling

13. [Optimization] Custom card guide text with dynamic height adaptation

14.[Optimization]Direct access to the API method for optimizing message history has been improved

15. [Optimization] Modify the display rules for product cards

16.[New]Large model robot adds successful and failed transfer-to-human prompts

17.[New]Large Model Robot to Human Rule Processing Logic

 

## Update Notes SDK-4.2.4_1 (2025-06-04)

1. [Optimization] Fix occasional drawing crashes on iOS 17 version

2. [Optimization] Optimize AiAgent Q&A message parsing

3.[Optimization]Optimize the sending method of large model robots, support quick questions and direct answers.

 

 

## Update Notes SDK-4.2.4 (2025-04-15)

1.[New]AiAgent supports like and dislike buttons

2.[New]AiAgent adds message card

3.[New]AiAgent supports satisfaction rating

4. [New] SDK adds button message type

5.[New]Add manual transfer strategy

6.[New]Robot multi-language: Supports satisfaction rating, thumbs up/down, and welcome message

7.[Optimization]Optimize the issue of hyperlink interception URL decode

8.[Optimization]Optimize the issue of quoted images in messages showing as loading when sent to the PC client

 

## Update Notes SDK-4.2.3 (2025-03-12)

1. [New] UI interface redesign

 

## Update Notes SDK-4.2.2 (January 9, 2025)

1. [New] Secondary Evaluation

2. [Optimization] Check the issue of abnormal parsing of the user online status interface

3.[Optimization]Email regular expression updated

4.[Optimization]Click the "Rebuild Session" button in the shortcut menu to re-fetch data and clear cached data.

5. [Optimization] Translation text optimization

 

## Update Notes SDK-4.2.1 (2024-12-20)

1.[New]Pre-chat form

2.[New]AiAgent supports MacDown format

3.[New]Add custom ticket status

4. [Optimization] Optimize the issue of missing emoji button while queuing

5.[Optimization]Optimize the issue with the thread for sending video network requests to the robot

6.[Optimization]Optimize the update of calling the system dialing API for iOS18

7.[Optimization]Optimize the issue where the bottom of the non-notch screen message record page is obscured

8.[Optimization]Optimize the logic for inviting session evaluation after ending a session

9.[New]Add custom fields when creating tickets with cards

 

## Update Notes SDK-4.2.0 (2024-11-01)

1.[New]Video playback supports dragging

2. [New] iOS18 adaptation

3.[New]aiAgent large model robot supports SSE

4.[New]Language Switching

5.[New]Initialization interface adds timezoneId, countryName fields

6.[New]Help Center Navigation Bar and Telephone Number Retrieval for PC Configuration

7. [Optimization] Optimization of mutual kicking issue

 

## Update Notes SDK-4.1.9 (2024-09-12)

1. [New] Satisfaction Template Migration

2.[New]Close the session, and next time continue with the previous customer service representative.

3.[New]Optimization of the overall solution for quick menu image development

4.[New]Navigation adaptation (When manual setup fails, display the company logo and name. If not configured, leave it blank)

5.[New]Replace special characters in announcement messages

6. [Optimization] Long connection reconnection optimization

 

## Update Notes SDK-4.1.8 (2024-07-16)

1.[New]New Message Reminder

2.[New]Add a combined date and time field to the message feature

3. [New] Add area code for mobile phone numbers in messages

4.[New]Add semantic transfer to human agent

5. [New] iOS 18 video system adaptation selection

6.[New]Hotspot Guidance Robot Q&A Parameter Compliance

7.[Optimization]Optimize the height of the image on the left side of the FAQ section

 

## Update Notes SDK-4.1.7 (2024-06-24)

1. [New] Feedback prompt for image saving

2.[New]Quick menu hyperlinks can append parameters

3.[New]Quick menu supports custom icons

4.[New]New messages display at the top by default

5.[New]Visitor-side unread message guidance for agents

6.[Optimization]Rules for Displaying Common Issue Images

 

## Update Notes SDK-4.1.5 (2024-05-14)

1.[New]Custom fields add a new city field

2. [Optimization] The scenario where the cursor automatically moves to the end of the content after deleting the textview component on the iOS13 system message page.

 

## Update Notes SDK-4.1.4 (2024-04-23)

1. [New] Reasons for Dislike

2. [New] Word Segmentation Association Switch

3.[New]General card optimization: Supports card recognition and automatic card push for customers

4.[New]Multi-session adds a node to transfer to human agent

5.[New]SDK Privacy Policy File PrivacyInfo.xcprivacy

6.[Optimization]cardLink click event, change ZCChatCellClickTypeOpenFile to ZCChatCellClickTypeOpenURL

7.[Optimization]Dutch: "Click to reconnect" = "Klik om opnieuw verbinding te maken"; changed to "Reload" = "Herladen";

8. [Optimization] The robot evaluation title and "Submit" do not use backend configuration, solving the issue where the robot evaluation title and "Submit" could not be internationalized.

9. [Optimization] Inaccurate translation of "Did this solve your problem?"

10. [Optimization] The robot evaluation input box issue will only display when unresolved, and will not display when resolved.

11. [Optimization] Refresh quick menu: Optimize queue, initialization, and chat entry checks

12. [Optimization] iOS 17 message has "updates", but it does not redirect to the message page.

 

## Update Notes SDK-4.1.3 (2024-03-19)

1.[New]Support for setting up transfer-to-human prompts

2. [Optimization] Custom card adaptation optimization

3.[Optimization]Unify the permission prompt box button, change the original "OK" to "Cancel"

 

## Update Notes SDK-4.1.2 (2024-02-02)


---

1. [New] Multi-round template style one supports multi-line display

2. [New] The new message page supports whether to display the problem description and whether the problem description is required.

3. [Optimization] Fix the issue where the preview of uploaded video in messages cannot play

4. [Optimization] Optimize the logic for whether the evaluation of "Resolved" or "Unresolved" is required and whether it should be displayed.

5. [Optimization] Push message filters HTML tags

 

## Update Notes SDK-4.1.1 (2023-12-22)

1. [New] Support for message quoting feature

2. [New] Supports read/unread status for messages

3. [Optimization] Page echo issue when recalling messages

4. [Optimization] Page status display issue when the session ends abnormally

 

## Update Notes SDK-4.1.0 (2023-12-08)

1. [Optimization] Abnormal call of UIGraphicsBeginImageContextWithOptions method on iOS 17 system

2. [Optimization] The issue where system-recorded videos and audio on iOS17 fail to save successfully in the local sandbox.

3. [Optimization] The issue of no audio recording when shooting videos

 

 

## Update Notes SDK-4.0.9 (November 2, 2023)

1. [Optimization] Inaccurate traditional Chinese translation in internationalization files optimized

2. [Optimization] Rich text merge and line break optimization

3. [Optimization] Optimization of keyword-based transfer to human agent logic

 

## Update Notes SDK-4.0.8 (2023-9-19)

1. [New] Dutch translation

2.[New]Message Satisfaction Rating

3. [Optimization] File URL containing Chinese characters and JPEG image format not recognized in message replies

 

## Update Notes SDK-4.0.7 (2023-8-29)

1. [New] Add a default unselected state for ratings

2. [New] If the delayed transfer to manual queue fails to call the new API or is unsuccessful, the message will automatically be converted to an offline message.

3.[Optimization]Translation optimization for the system message when thumbs-down leads to human service

 

## Update Notes SDK-4.0.6 (2023-07-17)

[Optimization]Synchronize custom card code, change from 20 to 21

 

## Update Notes SDK-4.0.5 (2023-06-30)

[New]Support for sending custom cards

[New]The robot supports sending images, files, and videos.

[New]End session supports pop-up evaluation invitation

[New]Support for functions such as transferring to human agent groups via keywords

[New]Synchronize multi-round ticket collection node

[New]UI Revision for Message Record List Page

[New]Robot point-down interface adds statistical parameter gptAnswerType

[Optimization] The issue of inconsistent historical records when pulling down the history log

[Optimization] Send txt file, view it on the file preview page, and then return to report an issue.

[Optimization]iOS11 System Network Request Exception Issue

[Optimization] Clicking on the invitation to rate pops up the rating page. If you close the rating page without rating, the invitation does not reset to the default star rating score.

[Optimization] The issue where the product card parameters are cleared and a blank screen is displayed after sending the product card.

[Optimization] Jump to the message page, the issue of template selection being invalid

 

## Update Notes SDK-4.0.4 (2023-06-01)

[New]Rich text tag support for welcome messages

[New]After ending the session, hide the quick menu

[New] Enable the display of the transfer-to-human button with the isShowTransfer and unWordsCount attributes.

[Optimization] Custom color adaptation for the navigation bar and button display issues

[Optimization] Issue with navigation name display after customer service transfer

[Optimization] Chat message blocking issue

[Optimization] Adjustment of display details for order card and product card

[Optimization] Judgment for repeated button clicks

[Optimization]Adaptation for landscape and portrait screen switching

[Optimization] Multilingual Ultra-long Character Display Adaptation

[Optimization] Change the video file sending limit to 50M, replace the video conversion solution, and improve the user experience.

[Optimization] Clean up invalid custom UI attributes

 

## Update Notes SDK-4.0.3 (2023-04-06)

[New]Order card supports custom fields

[New]Manual Voice to Text

[Optimization] Multilingual Translation Synchronization

[Optimization] Close and replace with button

[Optimization] When sending a video, you can request permission separately. If there is no microphone, you can send an image.

[Optimization] Modify the way to specify internationalized language for the interface

[Optimization] Add a new configuration for the appinit interface to display a customer service welcome message for new users.

 

## Update Notes SDK-4.0.2 (2022-12-26)

[Optimization] Navigation Adaptation

[Optimization]Message UI Adaptation

 

## Update Notes SDK-4.0.1 (2022-12-8)

[Optimization] SDK Landscape Adaptation Optimization

 

## Update Notes SDK-4.0.0 (November 3, 2022)

[New]Upgrade SDK to adapt to V6 account features

[New]Support personalized display effects for visitors on the backend

[New]Support for configuring multi-functional shortcut menus

[New]Support for the new version of FAQ

 