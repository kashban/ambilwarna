ambilwarna
==========

This is a clone of https://code.google.com/p/yuku-android-util/source/browse/#git%2FAmbilWarna ,
created to migrate the project from Eclipse to Android Studio (and gradle).

Credit for all code in this project goes to:

  https://code.google.com/p/yuku-android-util/people/list


Installation
============

Note: These instructions are based on Android Studio 0.2.10. It is possible (likely?) that
you will need to adapt these instructions for later versions.

* Clone this repo. For example:

        git clone https://github.com/therealdpk/ambilwarna

* Open Android Studio. Click Import Project (or File Menu -> Import Project).
* Navigate to your project clone in the Select Gradle Project Import dialog and hit OK.
* Choose "Use default gradle wrapper" (the recommended option).
* Build and install the AmbilWarna aar file that you'll be using in your project.
    * Open the Gradle tasks pane in AS by clicking the "Gradle" button. By default the button is rotated vertically and found along the right side of the screen.
    * You should see a navigation tree starting just below the text "All Tasks". Click the plus to expand the tree.
    * Double click the "install" task.
    * The Run pane will now open. You should see "BUILD SUCCESSFUL". There is now a ambilwarna .aar file available for use in your local maven repository.
* Open your project (the one to which you want to add AmbilWarna).
* Find the build.gradle file that already contains build instructions. In some projects there is an empty build.gradle file at the root and a populated gradle.build file in a subdirectory.
* Edit the build.gradle file. You'll be adding instructions to use the local maven repository and adding the AmbilWarna aar as a compile dependency.

        # This is a sample of a build.gradle file that includes AmbilWarna's .aar.
        buildscript {
            repositories {
                mavenLocal() # <- new line
                mavenCentral()
            }
            dependencies {
                classpath 'com.android.tools.build:gradle:0.5.+'
            }
        }
        apply plugin: 'android'
        
        repositories {
            mavenLocal() # <- new line
            mavenCentral()
        }
        
        android {
            compileSdkVersion 18
            buildToolsVersion "17.0.0"
        
            defaultConfig {
                minSdkVersion 7
                targetSdkVersion 18
            }
        }
        
        dependencies {
            compile 'yuku.ambilwarna:AmbilWarna:1.0@aar' # <- new line
        }

* That's it. Please see the official documentation to learn how to include the AmbilWarna code in your project: https://code.google.com/p/android-color-picker/
