# Create-A.I.-Using-Python
import pyttsx3
import speech_recognition as sr
import datetime
import wikipedia
import webbrowser as wb
import os
import smtplib
import psutil
import pyjokes
import pyautogui
import pyaudio
import random
import json
import requests
from urllib.request import urlopen
import wolframalpha
import time
import numpy as np

wolframalpha_app_id = 'your app id'
engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[0].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()

def wishMe():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good morning sir!")

    elif hour>=12 and hour<18:
        speak("good Afternoon sir!")

    else:
        speak("good morning sir!")

    speak("Welcome Sir, jarvis at your service. please tell me how may i help you!")

def takeCommand():
    #It takes microphone input from the user and returns string output

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_thershold = 1
        audio = r.listen(source) 

    try:
        print("Recognizing...")
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")

    except Exception as e:
        print(e)
        print("say that again please....") 
        return "None"
    return query

def sendEmail(to, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
    server.starttls()
    server.login('Your Email I'D', 'Your Email Pass')
    server.sendmail('write email who you want to send the email', to, content)
    server.close()

def cpu():
    usage = str(psutil.cpu_percent())
    speak('CPU is at'+usage)

    battery = psutil.sensors_battery()
    speak('Battery is at')
    speak(battery.percent)

def joke():
    speak(pyjokes.get_joke())

def screenshot():
    img = pyautogui.screenshot()
    img.save('D:\\Games\\ScreenShot\\screenshot.png')


if __name__ == "__main__":
    wishMe()
    while True:
        query = takeCommand().lower()

       
        # logic for executing tasks based on query
        if 'wikipedia' in query:
            speak('Searching Wikipedia...')
            query = query.replace("wikipedia", "")
            results = wikipedia.summary(query, sentences=2)
            speak("According to Wikipedia")
            print(results)
            speak(results)

        elif 'how are you' in query:
            speak('I am fine, sir thanks for asking, how are you sir, I hope you get well soon')

        elif 'thank you' in query:
            speak('Welcome sir, i hope you are safe.!!')

        elif 'according to you who am i' in query:
            speak('if you can talk, than definatly you are a human')

        elif 'search in youtube' in query:
            speak('what should i search?')
            chromepath1 = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
            search_Term = takeCommand().lower()
            speak('Here we go to YOUTUBE!')
            wb.get(chromepath1).open("https://www.youtube.com/results?search_query="+search_Term)
        
        elif 'search in chrome' in query:   
            speak('what should i search?')
            chromepath = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
            search = takeCommand().lower()
            wb.get(chromepath).open_new_tab(search+'.com')
        
        
        elif 'search in google' in query:
            speak('What should i search?')
            chromepath2 = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
            search_Term1 = takeCommand().lower()
            speak('searching....')
            wb.get(chromepath2).open("https://www.google.com/search?q="+search_Term1)


        elif 'write song name' in query:
            music_dir = 'D:\\Games\\songs'
            speak("ok sir, start play"Write song name", enjoy sir.!!")
            songs = os.listdir(music_dir)
            print(songs)
            os.startfile(os.path.join(music_dir, songs[0]))

        elif 'write song name' in query:
            music_dir2 = 'Selecte youe songs folder path where you create'
            speak("ok sir, start play "write song name", enjoy sir.!!")
            p_songs = os.listdir(music_dir2)
            print(p_songs)
            os.startfile(os.path.join(music_dir2, p_songs[0]))


        elif 'write song name' in query:
            music_directory = 'same as here'
            speak("ok sir, start play "write song name", enjoy sir..!!")
            Play_songs = os.listdir(music_directory)
            print(Play_songs)
            os.startfile(os.path.join(music_directory, Play_songs[0]))

        elif 'play write song name' in query:
            music_dir1 = 'same as here'
            speak("ok sir, start play "write song name", enjoy sir.!!")
            Playing_song = os.listdir(music_dir1)
            print(Playing_song)
            os.startfile(os.path.join(music_dir1, Playing_song[0]))

        elif 'play write song name' in query:
            music_dir4 = 'same as here'
            speak("ok sir, start play "write song name", enjoy sir.!!")
            Playing_song4 = os.listdir(music_dir4)
            print(Playing_song4)
            os.startfile(os.path.join(music_dir4, Playing_song4[0]))

        elif 'write song name' in query or 'play again' in query:
            music_dir4 = 'same as here'
            speak("ok sir, start play song, enjoy sir.!!")
            Playing_song4 = os.listdir(music_dir4)
            print(Playing_song4)
            os.startfile(os.path.join(music_dir4, Playing_song4[0]))

        elif 'play music' in query:
            music_dir3 = 'same as here'
            music = os.listdir(music_dir3)
            speak('what should i play sir?')
            speak('select a song..')
            ans = takeCommand().lower()
            while('number' not in ans != 'anyone' and ans != 'your choice'):
                speak('I could not uderstand you. Please Try Again.!')
                ans = takeCommand().lower()
            if 'number' in ans:
                no = ans.replace('number', '')
            elif 'anyone' or 'your choice' in ans:
                no = random.randint(1, 7)
                os.startfile(os.path.join(music_dir3, music[no]))
            
        elif 'time' in query:
            strTime = datetime.datetime.now().strftime("%H:%M:%S")
            speak(f"Sir, the time is {strTime}")

        elif 'the date' in query:
            year = datetime.datetime.now().year
            month = datetime.datetime.now().month
            date = datetime.datetime.now().day
            speak('sir, the date is')
            speak(date)
            speak(month)
            speak(year)

        elif 'cpu' in query:
            cpu()
           
        elif 'joke' in query:
            joke()

        elif 'open steam' in query:
            speak('ok sir, Opening steam...')
            cauntar_trike = r'C:\\Program Files (x86)\\Steam\\steam.exe'
            os.startfile(cauntar_trike)

        elif 'screenshot' in query:
            screenshot()

        elif 'open code' in query:
            codePath = "C:\\Users\\hp\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
            os.startfile(codePath)
        
        elif 'remember that' in query:
            speak("what should i remember sir?")
            memory = takeCommand()
            speak("You asked me to remember that"+memory)
            remember = open('memory.txt','w')
            remember.write(memory)
            remember.close()
        
        elif 'do you remember anything' in query:
            remember = open('memory.txt','r')
            speak('You asked me to remember that'+remember.read())

        elif 'entertainment news' in query:
            try:
                jsonObj = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=entertainment&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj)
                i = 1
                
                speak('Here are some top headlines from the Entertainment Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1
            
            except Exception as e:
                print(str(e))

        elif 'business news' in query:
            try:
                jsonObj1 = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=business&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj1)
                i = 1
                
                speak('Here are some top headlines from the business Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1
            
            except Exception as e:
                print(str(e))

        elif 'health news' in query:
            try:
                jsonObj2 = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=health&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj2)
                i = 1
                
                speak('Here are some top headlines from the health Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1
            
            except Exception as e:
                print(str(e))

        elif 'science news' in query:
            try:
                jsonObj3 = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=science&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj3)
                i = 1
                
                speak('Here are some top headlines from the science Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1
            
            except Exception as e:
                print(str(e))

        elif 'sports news' in query:
            try:
                jsonObj4 = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=sports&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj4)
                i = 1
                
                speak('Here are some top headlines from the sports Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1
            
            except Exception as e:
                print(str(e))

        elif 'technology news' in query:
            try:
                jsonObj5 = urlopen("http://newsapi.org/v2/top-headlines?country=in&category=technology&apiKey=7fb1cf7a9e3e46e7a716a691f4a1b0f8")
                data = json.load(jsonObj5)
                i = 1

                speak('Here are some top headlines from the technology Industry')
                print('==========TOP HEADLINES=========='+'\n')
                for item in data['articles']:
                    print(str(i)+'. '+item['title']+'\n')
                    print(item['description']+'\n')
                    speak(item['title'])
                    i += 1

            except Exception as e:
                print(str(e))
        
        elif 'where is' in query:
            query = query.replace("where is","")
            chromepath2 = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
            location = query
            speak("User asked to locate"+location)
            wb.get(chromepath2).open_new_tab("https://www.google.com/maps/place/"+location)

        elif 'calculate' in query:
            client = wolframalpha.Client(wolframalpha_app_id)
            indx = query.lower().split().index('calculate')
            query = query.split()[indx + 1:]
            res = client.query(''.join(query))
            answer = next(res.results).text
            print('The Answer is : '+answer)
            speak('The Answer is '+answer)

        elif 'what is' in query or 'who is' in query:
            client = wolframalpha.Client(wolframalpha_app_id)
            res = client.query(query)
            try:
                print(next(res.results).text)
                speak(next(res.results).text)
            except StopIteration:
                print("No Results")

        elif 'stop listening' in query:
            speak('For How many second you want me to stop listening to your commands?')
            ans = int(takeCommand())
            time.sleep(ans)
            print(ans)

        elif 'show my location' in query or 'where we are' in query:
            speak("wait sir, let me check")
            try:
                ipAdd = requests.get('https://api.ipify.org').text
                print(ipAdd)
                url = 'https://get.geojs.io/v1/ip/geo/'+ipAdd+'.json'
                geo_requests = requests.get(url)
                geo_data = geo_requests.json()
                #print(geo_data)
                city = geo_data['city']
                # state = geo_data['state']
                country = geo_data['country']
                speak(f"sir i am not sure, but i think we are in {city} city of {country} country")
            except Exception as e:
                speak("sorry sir, Due to network issue i am not able to find where we are.")
                pass
                        
        elif 'log out' in query:
            os.system("shutdown -l")

        elif 'restart' in query:
            os.system("shutdown /r /t 1")

        elif 'shutdown' in query:
            os.system("shutdown /s /t 1")

        elif 'email to sender name' in query:
            try:
                speak("what should I say?")
                content = takeCommand()
                to = "sender Email Id"
                sendEmail(to, content)
                speak("email has beem send successfuly!")
            except Exception as e:
                #print(e)
                speak("sorry sir, I am not able to send this email")
        

        elif 'good bye' in query or 'bye' in query:
           user = "Going offline, by sir.!!"
           speak(user)
           exit()

     
