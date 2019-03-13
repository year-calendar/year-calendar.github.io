---
title: Home
layout: default
filename: /
--- 

Year calendar is a javascript widget that helps you create great calendars !


![Calendar](/assets/img/calendar.png)


The library is available for:
{% for library in site.data.libraries %}
- [{{ library.name }}](/{{ library.library }}/getstarted)
{% endfor %}