---
draft: false
toc: true
preview: false
author: Pramita Ayu
lastmod: 2022-01-25T05:00:50+09:00
title: Live
name: Live
date: 2023-06-10T21:23:32.237Z
thumbnail: /uploads/2022/01/25/aplikasi-sadap-terbaik.png
type: demo
layout: single


fitur_live: true
pre: fa fa-video-camera


tbody:
  data:
    - name: Video
      pre: fa-video-camera
      checked: true
      list_camera:
      - name: Rear camera
        data_target_modal: "rearcamlive"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_430,e_volume:-80/v1722867768/907408051847_rear.webm
      - name: Front camera
        data_target_modal: "frontcamlive"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_430,e_volume:-80/v1722867768/907408051419_front.webm
      list_sound:
      - No sound
      - With sound (default mode)
      - With sound (communication mode) 
      list_mode:
      - Invisible mode
      - Visible mode
      - Invisible mode 2
      - Visible mode 2
      list_session:
      - 1
      - 2
      - 3
      - 4
      - 5
    
    - name: Audio
      pre: fa-file-audio-o
      list_sound:
      - name: With sound (default mode)
        data_target_modal: "defaultmode"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_200,e_volume:-90/v1722867768/202408051836_audio_1.webm
      - name: With sound (communication mode)
        data_target_modal: "communicationmode"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_200,e_volume:-95/v1722867768/302408051998_audio_2.webm
      list_mode:
      - Invisible mode
      - Visible mode
      - Invisible mode 2
      - Visible mode 2
      list_session:
      - 1
      - 2
      - 3
      - 4
      - 5
    
    - name: Screen
      pre: fa-desktop font-red-sunglo
      list_sound:
      - name: No Sound
        data_target_modal: "nosound"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_430,e_volume:-100/v1722867768/202408051836_screen_1.webm
      - name: With sound (default mode)
        data_target_modal: "defaultmode"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_430,e_volume:-80/v1722867768/98234104829_screen_2.webm
      - name: With sound (communication mode)
        data_target_modal: "communicationmode"
        file: https://res.cloudinary.com/dh6y6mugt/video/upload/c_fit,h_430,e_volume:-60/v1723269935/82718439293_screen_3.webm
        meta: Warning, this mode makes it possible to have a better sound on some telephones but can block the reading of a video or a music.
      list_mode:
      - Invisible mode
      - Visible mode
      - Invisible mode 2
      - Visible mode 2
      list_session:
      - 1
      - 2
      - 3
      - 4
      - 5
---


{{< demo/live >}}


