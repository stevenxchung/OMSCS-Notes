# Lesson 7

In this lesson we will go over the **Android** system - an operating system designed for mobile devices. Specifically we will cover the conceptual and practical aspects of Android.

## Android Introduction

What is Android? Android is:

1. Designed for mobile devices
2. Based on the Linux Kernel
3. Powered by the [Dalvik VM](<https://en.wikipedia.org/wiki/Dalvik_(software)>)

## Basic Architecture Of Android

The architecture of android beginning with the highest level is:

1. Apps
2. Application Framework
3. Libraries and Android runtime
4. Linux kernel

## Android App

The Android app is comprised of:

1. **Activities**: independent components such as a single screen with a user interface; can work together to form a cohesive whole
2. **Services**: a component that typically performs long running operations in the background such as a service for playing music or a downloading files
3. **Content provider**: provides a structure interface to a set of data such that data can be provided to various applications
4. **Broadcast receiver**: a receiver that could be registered to receive system or application events

Each one of the above components is connected by _intents_ and all component properties are declared in the Android manifest `.xml` file
