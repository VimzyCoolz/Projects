 MemeLord Structure
 
# 1. TABS(bottom)
   *Home
     *Share
    *profile
    *inbox
    *3lines hamburger 'menu'
     
    home-upload-profile-inbox-menu:these tabs must appear written and iconed ie icon on top and name below it.
                             
                        
   
# 2. SUBTABS.
   *2.0 Home  
           *Memes for you
           *Quotes for you
           *following
           *friends (status on top horizontal in circles then friends post vertically) ie status👉 and posts👇

on home tab there will be full search bar button suggesting what user may like to search particularly on that post. like how TikTok search behaves. still on home-top left there will be a name Memelord and it's logo then next to it is search bar


  *2.1 Share *upload from device (accept multiple photo uploads and remember to sort them one full view each ie scrollable horizontally and indicate which one is on the view ie 2/5. we can also indicate auto switch for multi photo posts after 5 seconds)
       *generate(this page will have text editor and background colour change. like that of facebook).
       
 
when user clicks next, ask them"upload to","1.Meme 2.quotes 3.status" if they select a meme give them the final stage "to select a sound"(optional) then change next button to "upload". but if they select quote there is no need for sound(this stage{sound stage} will be skipped when they select quote). don't forget to include 'description caption' field(15words) just at where last stage of uploading will be, which will be optional fill then if filled it will appear before the image not under. ie description then photo. we are implementing 15 words limit so as we maintain photo first app
       *Status will be shared to only users who follow each other. status expire after 24hours.
       *User can select meme or quote and status ie 1&3 or 2&3. in short only status can be compatible with memes and quotes


   *2.2 Profile 
    *here you will show 
      *1.profile picture 
      *2.Bio 
      *3.followimg 
      *4.followers 
      *5.overall likes,post,views 
      *6.liked(post that the user has liked, user can set it private/public) 
      *7.favoirite(post that he has maked as favourite,user can set it as private or public) 
      *8.reposts
      *9'account health' in percentage. eg the one with 0 report has 100%health and the one with 50reports have 0%health-this is                    automatically banned.
      *10 show metric button. this feature will show the user how their post are performing. eg how many followers they had on that                 post,likes,view, are they rising or dropping? through metric graphs.
   
   when user signin/up change profile icon to user's profile picture.
        *make this profile icon slightly larger than the other icons because it's at the center


   *2.3 inbox 
        *any communication made must be visible here also whether it's email,push or inapp notification.  
       *notify user about "new comment,like,follow,users who marked their video as favourite,downloaded or shared. the notification               should look like this {user}liked your video
       *auto deleted after 14days. but if the day to be deleted has come and user have not read the notification, it will also be deleted         but sent as email instead.
       *all likes,comment should be sent to user's phone push notifications as well.     
      
   *2.4 3lines humburger 'menu' 
                                    *Settings *dark/light mode toggle
                                    *edit profile+password
                                    *show/hide online status
                          *privacy policy(this link will be fetched from .env file (memelord_policy).
                          *show '©CoolzTech' at very bottom 
                          *Request verification badge through :upload national official document(s), then pay amount set by Controll app      
                          *intelix guide # this will act as in app guide. this part is open for all users. eg when I ask it "do Memelord                                             have a setting to turn off online status?" it should look at app structure and guide the user                                             appropriately. on this intelix only answer app related questions.     
                          *display app version
                          
                          


#3         NOTE BETTER
    *3.1. What will be included on each post is main (like,comment,share,download), hiden on 3dots menu (report,favourite,repost,sound used(show sound by default) ) user's name (blue and bold, capitalized)with a "follow"blue function which  font should be different with that of the username eg VIMZYCOOLZ•follow and VIMZYCOOLZ•following VIMZYCOOLZ•friends respectively and where appropriate 
    *3.2. when user download it ,it should be saved together with watermark of app name and uploaders user's name eg Memelord@VimzyCoolz this should be blurred because it should appear vertically from bottom left to top right)
    *3.3. detect when screenshot is taken inside the app. when it detect someone trying to screenshot offer them "we prefer you downloading the post because of high quality and originality" then offer a download button
    *3.4. the posts should not be sorted in latest form unless the algorithm suggest it. the app should have it's algorithm (like that of TikTok)
    *3.5. Admin is the one to upload sounds
    *3.6. Make sure the app will be compatible with another app(Memelord Controll)-this will be the admin of the app
    *3.7. This app will be AI powered.(like that of X where people type @grok for it to answer.) but mine will be @intelix. when verified user type "@intelix" then prompt in comment section the ai should reply to that comment. only when the user is verified
    *3.8. Algorithm should give automatically blue verified badge for users who hit 10,000 followers(or any other that the controll app will set) and the account must be 5month old and have not less than 80% account health
    *3.9. blue verified badge is for automatically verified, golden verified badge is only given by controll app
    *3.10. CEO username will have golden name and a blue verified badge
    *3.11. we will use Gmail API refresh token as email service.
    *3.12. user should not be locked in uploading screen, but also should not be blind of where their posts have reached to uploaded, so we will implement small uploading bar on top of home until the upload is complete 
    *3.13. when users long press any of the engagement buttons eg like/comment the function to open is to show users who have engaged to that button eg if I long press like button I will see people who have liked that particular post
    *3.14. accept name/underscores/numbers/fullstop/space only on username/signup
    *3.15. Signup will use email/username/password/bio/profile photo. send otp through email(Gmail refresh token). 
     *3.15.b for login is 1.username/email 2.password. below password field put a function 'forgot password' which triggered prompt the user to input 1.registered email/username 2.OTP sent to user email 3.change password 4.confirm above password *usernames will be unique and verify if the email/username is inside app's data in real time and when user clicks next field and there is no matched email/username show '{email/username} not registered yet! eg vimzycoolz@coolztech.com not registered yet!
    *3.16. when people share as link, the link should open the post itself as a view on where it's shared
    *3.17. we will connect our ai with duck duck go API so as it can have real time information 
    *3.18. when user likes or favourite a post it should be saved on users phone+cloud for anytime access even with no internet 
    *3.19. searched content should have separate tabs, this includes users,memes,quotes,etc
    *3.20. to elaborate better on 'friends' term used on this app: Incase user A follows user B and user B follow back user A, they became friends, so they can share status. secondly when I say friend's post-this is like filtering his feed to show only posts of users who are his friend.
    *3.21. this is a social meme app, so user's profiles are accessible by clicking the username but only shows public data like posts,reposts,profile picture,followers count, following count, friends etc
    *3.22. online status(small green circle on their profile pictures) should be included defaulted to on
    *3.23. I prefer a very clean and smooth UX and UI because memes require clarity while reading it
    *3.24. the title 'Memelord' should have separate font for each letter and letter 'o' should have two colours green and red. green for online and red for offline
    *3.25. main colours will be black, golden,purple,blue,green(dominant to be black and golden) but free to use others.
    *3.26. 5 seconds for splashing image to show. 


# 4    Next Project : Memelord Control
# 4.1 FUNCTIONS OF THIS APP
*4.1.1. See all users *4.1.2. send emails to users(either single or multiple or all)
*4.1.3. send push notifications 
*4.1.4. offer manually verification badge(like that of meta) to the users either blue or golden
*4.1.5. setting which any user who will hit set of followers will have automatically blue verified badge eg 10,000 followers
*4.1.6. choosing CEOs/special players who will have golden names
*4.1.7. mannually or automatically banning users who hit 0% account health and notifing the reported user throught email.
*4.1.8. manually or automatically  banning post when they reach 0% post health then notifying the user that their post have been banned due to excessive reports.
 both banns should have reversal only on this app.
*4.1.9. this app will be Communication Center(email,push,in app)
*4.1.10. uploading sounds and its name. also you can add a tag 'New' on recently uploaded sounds (< =7days)
*4.1.11. set verification amount for users who request it manually



#   Fetched Pro tips along my investigations
1. Do not "Hard Delete" status files immediately at 24 hours. Mark them as expired in the DB and use a Cron Job to batch-delete the actual media files from your storage bucket during low-traffic hours to save on I/O costs.
2. Pro Tip: The Master Moderation MatrixFinal Power = (Tier Base %) × (Behavior Multiplier) Tier Base %: Impact scales by seniority and status—0.5% for New Users (<14 days), 1% for Established (>14 days), 1.5% for Veterans (>30 days), 2% for Blue Verified, and 30% for Golden/CEO status. Behavior Multiplier: Your accuracy modifies your power—2.0x for "Good Samaritans" (confirmed reports), 1.0x for Neutral, and 0.5x for Trolls (false reports). In short that is how different users can reduce account health of user reported. same apply to post reposts
3. My sincere recommendation is I use native app for shell I use web native for it's content. Like how maybe Facebook use This will also make possible for users to access the app on both stores and web and devopers for over the air (OTA) update
4. 28. Most Important Principle 🚨Do NOT save:Plain text full provider-specific URLs inside database if possible.
5. Your app code should NEVER care whether storage is: Supabase MinIO AWS R2 Instead: your app should call something like: Plain text uploadSound() uploadImage() deleteMedia()
6. Implement Reporter Reputation. A report from a user with 100% health should carry more weight than a report from a new account or one with low health.
7. Since you want diagonal, semi-transparent watermarks, you shouldn't do this on the client side (phone) because it's CPU-intensive and can be bypassed. Production Path: Use a Serverless Function (AWS Lambda or Supabase Edge Function). When a user uploads, the function processes the image using a library like sharp, applies the watermark, and then saves it to storage.
8. Recommendation: Use a tiny, native ActivityIndicator (the spinning wheel) that only shows up during the very first download(splash screen). Once the file is cached, you never show that spinner again

