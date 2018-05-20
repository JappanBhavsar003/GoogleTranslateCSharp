# GoogleTranslateCSharp
This tutorial just show you that how to install google translate api and how to use it ! thank you
Hey guys in this repo i contains on program.cs file which will show you how to installed and setup google translate api

1. installed this from nuget package manager
   
// **Step 1 : Install Google.Cloud.Translation.V2 API from nuget package manager**
    
// **Step 2 : After Install Google.Cloud.Translation.V2 > Declare here**
    
    using Google.Cloud.Translation.V2;
    
// **Step 3 : Declare Google.Apis.Auth.OAuth2 for setting up google credentials**
    
    using Google.Apis.Auth.OAuth2;
   

    // Imp Note : Hey there you need to authenticate to google that you are accessing google's api so 
    
    //            You have to go https://cloud.google.com/translate/docs/reference/libraries and follow the 
    
    //            steps in description of this page shown you. It will redirect to service creation page and after creating
    
    //            service you have to download one JSON file

// **Step 4 : Inject System.IO for reading our downloaded JSON file.**
    
    using System.IO;

3. Main Logic

// **Step 5 : Define variable and real input from user**
            string userIP = "";
            string userLang = "";
            Console.Write("Hey there please enter some text here : ");
            userIP = Console.ReadLine();
            
// **You can refer all language from https://cloud.google.com/translate/docs/languages**
            
            Console.Write("Cool! now enter the language in which you want to translate your text: (Note please select from 'ru' , 'fr', 'gu', etc..)");
            userLang = Console.ReadLine();

// **Step 6 : Read JSON File (Which are we dowloaded earlier from Google cloud console)**
            
            StreamReader rdr = new StreamReader("C:\\Users\\Bhavsar\\Desktop\\PeachMap-9322d6cfe66d.json");
            string jsonStr = rdr.ReadToEnd();


// **Step 7 : Create Google credential object**
            
            var cred = GoogleCredential.FromJson(jsonStr);


// **Step 8 : Create TranslationClient Class Object for translating the text into specified language**
            
            TranslationClient client = TranslationClient.Create(cred);


            // **Step 9 : Create response for translate your text to specified language**
            // Imp Note : Please make sure that your are enable it from google cloud console (enable google translate api , actually i can't because it required billing lol!)
            // If you want to use for free you can refer: https://ctrlq.org/code/19909-google-translate-api
            // For c# free version you can refer: https://blogs.msdn.microsoft.com/shahpiyush/2007/06/09/translate-your-text-using-google-apis/
            
            var response = client.TranslateText(userIP, userLang);

            // **Step 10 : Show the translated language**
            
            Console.WriteLine("Your translated language is : ", response.TranslatedText);

            Console.ReadKey(); 
            
 This API conatins billing system 
 if you still want to use free version of this you can refer
 https://ctrlq.org/code/19909-google-translate-api
 and second one is
 https://blogs.msdn.microsoft.com/shahpiyush/2007/06/09/translate-your-text-using-google-apis/
