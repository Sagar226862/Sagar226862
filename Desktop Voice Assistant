import datetime
from pickle import TRUE
import webbrowser
from winreg import QueryInfoKey, QueryReflectionKey
import pyttsx3
import speech_recognition as sr
import os
import wikipedia
import smtplib
import cv2

engine =  pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
# pipprint(voices[0].id)
voices = engine.setProperty('voices', voices[0].id)

def speak(audio):          #  it imports the audio file by which the project will speak
    engine.say(audio)
    engine.runAndWait()

def wishMe():               # for wishing the user when he start thr project
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good Morning")
    elif hour>=12 and hour<18:
        speak("Good Afternoon")
    else:
        speak("Good Evening")
    speak("I am robot sir. please tell me how may I help you")

def takeCommand():          #it is for voice input from the user
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("listening...")
        r.pause_threshold = 1
        audio = r.listen(source,timeout=1,phrase_time_limit=5)

    
    try:
        print("Recognizing...")
        query = r.recognize_google(audio,language='en.in')
        print(f"user said: {query}\n")

    except Exception as e:
        print(e)
        speak("say that again please...")
        query="Nothing"
        
    return query
    
    def sendEmail(to, content):
         server = smtplib.SMTP('smtp.gmail.com',587)
         server.ehlo()
         server.starttls()
         server.login('sagargohil643@gmail.com','your-password')
         server.sendmail('youremail@gmail.com',to,content)
         server.close()
        

if __name__ == "__main__":
    wishMe()
    query = takeCommand().lower() #1st time input
    while True:
        if 'new command' in query:
            speak("I am awaiting commond.")
            query = takeCommand().lower()
            #logic for executing tasks based on query 
        elif 'sleep' in query:
            speak("Good Bye.")
            break
            # goodbye ----            
        elif 'wikipedia' in query:
            speak('searching wikipedia...')    
            query = query.replace("wikipedia","")
            results = wikipedia.summary(query,sentences=2)
            speak("according to wikipedia")
            print(results)
            speak(results) 
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()
        elif 'open youtube' in query: 
            webbrowser.open("youtube.com")
            speak("Youtube is opened, Enjoy your Videos")
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()

        elif 'open google' in query: 
            webbrowser.open("google.com")
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()

        elif 'open stackoverflow'  in query:
            webbrowser.open("stackoverflow.com")
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()

        elif 'the time' in query:
            strTime = datetime.now().strtime("%H:%M:%S")
            speak(f"sir,the time is {strTime}")
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()

        elif 'open command prompt' in query:
            os.system("start cmd")
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()
        
        elif 'open camera' in query:
            cap = cv2.VideoCapture(0)
            while TRUE:
                ret, img = cap.read()
                cv2.imshow('webcam',img)
                k = cv2.waitkey(50)
                if k==27 :
                    break;
                cap.release()
                cv2.destroyAllWindows()
            query = " "
            speak("I am awaiting Commond.")
            query = takeCommand().lower()

        else :
            speak("Sorry, I am unable to understand. Please speak again")
            query = " "
            query = takeCommand().lower()

