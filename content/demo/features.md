---
draft: false
toc: true
preview: false
author: Pramita Ayu
lastmod: 2022-01-25T05:00:50+09:00
title: Features
name: Features
date: 2023-06-10T21:23:32.237Z
thumbnail: /uploads/2022/01/25/aplikasi-sadap-terbaik.png
type: demo
layout: single

features: true
btn_onoff: true
pre: fa fa-cogs


menu:
  demo:
    name: Features selection
    parent: account
    pre: fa fa-cogs
    weight: 2

tbody:
  data:
    fitur:
    - name: Send the data* that is not yet transmitted to the account all
      pre: fa fa-database
      list:
      - hour: 
        minute: 15
      - hour:
        minute: 30
      - hour: 1
        minute: 
      - hour: 2
        minute:
      - hour: 4
        minute:
      - hour: 8
        minute:
      - hour: 16
        minute:
      - hour: 24
        minute: 
      
    fitur_1:
    - name: SMS
      pre: icon-envelope
    - name: MMS
      pre: fa fa-file-image-o
    - name: Calls
      pre: fa fa-phone
    - name: Recording calls
      pre:


    config_type:
    - name: Configuration type*
      list:
      - name: Native
        id: native
      - name: Android Recorder
        id: androidRecorder
      - name: NativeX
        id: nativeX
      - name: Media Recorder
        id: mediaRecorder

    native:
    - name: Type of audio file*
      id: native
      mp3: true
      amr: true
      mav: true
      mp4: false
      acc: false
      3gp: false


    android_recorder:
    - name: Audio source*
      id: androidRecorder
      mic: true
      voice_call: true
      voice_downlink: true
      voice_uplink: true
      voice_communication: true
      camcorder: true
      voice_recognition: true
    - name: Type of audio file*
      id: androidRecorder
      mp3: true
      amr: true
      mav: true
      mp4: false
      acc: false
      3gp: false
    
    nativex: 
    - name: Type of audio file*
      id: nativeX
      mp3: true
      amr: true
      mav: true
      mp4: false
      acc: false
      gp3: false
    

    media_recorder:
    - name: Audio source*
      id: mediaRecorder
      mic: true
      voice_call: true
      voice_downlink: true
      voice_uplink: true
      voice_communication: true
      camcorder: true
      voice_recognition: true
    - name: Type of audio file*
      id: mediaRecorder
      mp3: false
      amr: true
      mav: false
      mp4: true
      acc: true
      gp3: true
      
    size_limit_call:
    - name: Recording file size limited to the calls when sending over 3G/4G
      list:
      - name: 1
        selected: false
      - name: 2
        selected: false
      - name: 3
        selected: false
      - name: 4
        selected: false
      - name: 5
        selected: false
      - name: 10
        selected: true
      - name: 20
        selected: false
      - name: 30
        selected: false
      - name: 60
        selected: false
      - name: 100
        selected: false
      - name: 200
        selected: false
      - name: 500
        selected: false

    fitur_2:
    - name: Locations
      pre: icon-map

    send_position:
    - name: Send position all
      minute:
      - 15
      - 30
      hour:
      - 1
      - 2
      - 4
      - 8
      - 16
      - 24
    
    fitur_3:
    - name: Automatically activate hands free speaker (Be careful it can disable bluetooth headset)
      pre: 
    - name: Increase sound calls
      pre: 
    - name: Use only the WiFi to send calls
      pre: 

    fitur_6:
    - name: Using GPS for location
      pre: 
    - name: Pictures
      pre: icon-picture
    - name: Apps
      pre: icon-game-controller
    - name: Blocking Apps
      pre: icon-game-controller
    - name: Site
      pre: fa fa-chrome
    - name: Blocking Site
      pre: icon-ban
    - name: Calendar
      pre: fa fa-calendar
    - name: Contacts
      pre: icon-notebook
    - name: Screenshot
      pre: fa fa-binoculars


    fitur_7:
    - name: Facebook
      pre: icon-social-facebook
    - name: WhatsApp
      pre: fa fa-whatsapp
    - name: Instagram
      pre: fa fa-instagram
    - name: Hangouts
      pre: fa fa-comment-o
    - name: Viber
      pre: fa fa-volume-control-phone
    - name: Gmail
      pre: fa fa-google-plus
    - name: Kik
      pre: fa fa-comment-o
    - name: LINE
      pre: fa fa-commenting-o

    fitur_8:
    - name: Facebook
      pre: icon-social-facebook
    - name: WhatsApp
      pre: fa fa-whatsapp
    - name: Hangouts
      pre: fa fa-comment-o
    - name: Skype
      pre: fa fa-skype
    - name: Viber
      pre: fa fa-volume-control-phone
    - name: Gmail
      pre: fa fa-google-plus
    - name: Kik
      pre: fa fa-comment-o
    - name: LINE
      pre: fa fa-commenting-o
    - name: Tango
      pre: fa fa-commenting-o
    - name: Telegram
      pre: fa fa-paper-plane-o
    - name: WeChat
      pre: fa fa-wechat
    - name: Snapchat
      pre: fa fa-snapchat
    - name: Tinder
      pre: icon-fire
    - name: Hike
      pre: fa fa-commenting-o
    - name: Instagram
      pre: fa fa-instagram
    - name: imo
      pre: fa fa-commenting-o
    - name: Twitter
      pre: fa fa-twitter
    - name: YouTube
      pre: fa fa-youtube-play
    - name: Signal
      pre: fa fa-commenting-o
    
    fitur_9:
    - name: Take a picture if the password is incorrect
      pre: fa fa-file-picture-o
      sup: 3


    fitur_10:
    - name: Password SMS
      pre: fa fa-file-picture-o
      sup: 
      place_holder: passwordSMS
    - name: Password of the application
      pre: fa fa-file-picture-o
      sup: 4
      place_holder: "*1234*"
    - name: Phone name
      pre: fa fa-file-picture-o
      sup: 
      place_holder: John Doe

    fitur_11:
    - name: Quick navigation
      pre: fa fa-fighter-jet
      sup: 5





---
{{< demo/features >}}