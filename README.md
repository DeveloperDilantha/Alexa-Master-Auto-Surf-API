# Alexa-Master-Auto-Surf-API
Learn how to use Alexa Master Auto Surf API easily




# 1) First of all you have to "Sync"

GET CALL: https://www.alexamaster.net/api/v1/plugin_sync.php?master_id=[YOUR_MASTER_ID]

NOTE: You do not have to call this always. This will only show you that you can access the API or not.

Login to alexamaster account and find your Master ID (It can be found on the left side near your profile picture). Then replace [YOUR_MASTER_ID] in above link with your number. Please note it must be a number. If you put someone elses Master ID, it will not work well.

The above example will return a Json string that you can access using your app. 

{
"status":"success",
"end_ip":"{Your IP}",
"master_name":"{Your Name}",
"master_points":"{Your Points}"
}

If you get "success" status, it means you can start AutoSurf using the API. 





# 2) Start the Auto Surf using "Surf_Open"

GET CALL: https://www.alexamaster.net/api/v1/plugin_surf_open.php?long_query=new&master_id=[YOUR_MASTER_ID]

NOTE: Everytime you open AutoSurf, you must call this and the get the Json string that includes commands.

{
"status":"success",
"token":"{A secret token code}",
"url":"{Advertised URL}",
"points":"{Number of points you earn}",
"time":"{Keep the website opened this much seconds}",
"ref":"{Change browser Referrer string if this is not - }",
"ua":"{Change your device User Agent string if this is not - }",
"up_url":"{A web address to visit before advertised website}",
"up_time":"{how many seconds to stay on up_url}",
"down_url":"{A web address to visit after the given time of the Advertised URL}",
"down_time":"{how many seconds to stay on down_url}"
}

Step 01: If the "status" is "success", you have to visit the "up_url" for "up_time" seconds. 

Step 02: Then open the "url" and stay "time" seconds.

Step 03: After that, you have to visit the "down_url" for "down_time" seconds.

Please note: you have to do the surf like above. Your computer must visit all 3 websites (URLs) without blocking any content. If you fail to do it, the alexamaster system will add Bad Votes to your account. Also it can add IP Strikes.

IMPORTANT: Keep copied the "token" in your memory. We need it for the next call.




# 3) Earn your points using "Surf_Close"

GET CALL: https://www.alexamaster.net/api/v1/plugin_surf_close.php?long_query=[TOKEN]&master_id=[YOUR_MASTER_ID]

NOTE: To claim your points, you need to call this. Otherwise, system will not add points. 

What is [TOKEN]? This comes from the "Surf_Open"
