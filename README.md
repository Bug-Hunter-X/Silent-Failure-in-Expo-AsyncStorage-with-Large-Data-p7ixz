# Silent Failure in Expo AsyncStorage with Large Data

This repository demonstrates a subtle bug in Expo's AsyncStorage when storing large JSON objects.  AsyncStorage has size limitations, and exceeding those limits leads to silent failure. No error is thrown, which can be very difficult to track down.

## Problem

The issue arises when attempting to store a JavaScript object in AsyncStorage that exceeds its size limits. AsyncStorage does not throw an error, but simply fails to store the data.  This means that a seemingly successful `setItem` call might actually have failed.

## Solution

The solution is to implement data size checking before attempting to store the data. If the data is too large, an appropriate error message should be provided to the user, or an alternative storage mechanism (like Realm or SQLite) should be considered.