---
draft: false
toc: true
preview: false
author: Pramita Ayu
lastmod: 2022-01-25T05:00:50+09:00
title: Schedule Restriction
name: Schedule Restriction
date: 2023-06-10T21:23:32.237Z
thumbnail: /uploads/2022/01/25/aplikasi-sadap-terbaik.png
type: demo
layout: single



schedule_restriction: true
pre: fa fa-lock



thead:
- name: Type
  width: "67"
- name: Name
  width: "67"
- name: Message
  width: "329"
- name: Number
  width: "67"
- name: Date
  width: "119"
- name: Address
  width: "120"


tbody:
  data:
    - name: Sleep
      id: "01"
      status: true
      date: 2023-12-12
      start_date: 20:00
      end_date: 00:00
      message: Phone blocked - Sleep
      days:
        - Monday
        - Tuesday
        - Wednesday
        - Thursday
        - Friday
    - name: School
      id: "01"
      status: true
      date: 2023-12-12
      start_date: 08:00
      end_date: 12:00
      message: Phone blocked - Focus
      days:
        - Monday
        - Tuesday
        - Wednesday
        - Thursday
        - Friday
---

{{< demo/schedulerestriction >}}
