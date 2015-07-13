To install, just unzip FullBNT.zip, start Matlab, and then add
BNT to your path.
You can go to File->Set\_Path, and then click on "Add Folder with Subfolders" and select the bnt folder. Or you can cd to the directory containing BNT and execute the following

```
>> cd C:\kmurphy\FullBNT\FullBNT-1.0.4  % modify as needed
>> addpath(genpathKPM(pwd))
```



The genpathKPM function is like the builtin genpath function, but it does not add directories called 'Old' to the path, thus preventing old versions of functions accidently shadowing new ones. The warnings occur because Matlab 7 added functions with the same names as my functions. The BNT versions will shadow the built-in ones, but this should be harmless. (Note: the functions installC\_BNT etc. are not needed anymore: all C code has either been removed or is unnecessary.)

Now test your installation:

```
>> test_BNT
```

With new versions of matlab you will get lots of warning messages, but everything should still work.
In particular, you will definitely see a warning like this:
```
Warning: Function D:\Program Files\MatLab\Works\BNT\KPMtools\assert.m has the same
name as a MATLAB builtin. We suggest you rename the function to avoid a potential name conflict. 
```
This is harmless and can be ignored.

Note: Cory Reith tells me that, as of 15 Sep 2009, octave 3.2.2 can run most of BNT. Please send email to crieth@ucsd.edu if you have questions.