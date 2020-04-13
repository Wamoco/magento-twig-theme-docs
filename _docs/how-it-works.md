---
title: How it works
permalink: /docs/how-it-works/
---

The idea is not only to make Twig available as an alternative template rendering engine in Magento. There are already modules to accomplish this, e.g. [Magento2-Twig](https://github.com/SchumacherFM/Magento2-Twig). Our approach goes beyond that and features a way to exchange entire pages. There is no need to rely on cumbersome xml layout updates to modify page structure which is always a struggle for Frontend Developers not familiar with Magento.

Twig itself is very simple. Some basic things are required, like control structures, output variables and include some other templates. Thats all. But where and how is the data accessible you ask?

This is, where the magic comes in. This module provides a bridge to access all required data from Magento in your Twig templates. It doesnt matter from which Helper, or Block this data is coming from. By using some provided functions and filters you will be able access everything.

