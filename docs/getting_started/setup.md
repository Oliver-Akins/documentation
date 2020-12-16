
# Setting up your development environment

There is an easy way and a hard way to get started with developing on the Conduit platform. We'll start with the easy way.

### Easy Way

Create a new Gradle project in your preferred IDE and set the contents of your `build.gradle` to the following:

```java

buildscript {
    repositories {
        jcenter()
        maven {
            url "https://repo.conduit.systems/repository/releases/"
        }
    }

    dependencies {
        classpath "systems.conduit:Stream:1.0.2"
    }
}

apply plugin: "Stream"

conduit {
    minecraft = "20w49a"  // Change this to whatever version of Minecraft you're developing for
    version = "0.0.6"  // Change this to the corresponding version of Conduit for the Minecraft version
    java = "1.8"
}

```

Then, Stream, Conduit, and their dependencies will start automatically resolving. After that, Stream will decompile and remap the Minecraft source code. This step may take a while!

Once this has completed, you're ready to move on to the [next section](getting_started/your_first_plugin.md)!

### Hard way

The hard way involves manually compiling both Stream and Conduit. This isn't exactly difficult, but it will take a bit longer.

First, start by cloning & compiling the latest version of Stream

```bash
git clone https://github.com/ConduitMC/Stream
cd Stream
./gradlew install
```

Once this completes, clone & compile the latest version of Conduit

```bash
git clone https://github.com/ConduitMC/Conduit
cd Conduit
./gradlew install
```

Once this completes, you've successfully installed the latest version of Stream and Conduit locally!

Now, you're ready to create a new Gradle project in your favorite IDE. Once you've done so, set the contents of your `build.gradle` to the following:

```java

buildscript {
    repositories {
        jcenter()
        mavenLocal()
    }

    dependencies {
        classpath "systems.conduit:Stream:1.0.2"  // Change this version to whatever version of Stream you've built
    }
}

apply plugin: "Stream"

conduit {
    minecraft = "20w49a"  // Change this to whatever version of Minecraft you're developing for
    version = "0.0.6"  // Change this to the corresponding version of Conduit for the Minecraft version
    java = "1.8"
}

```

Now you're ready to move on to the [next step](getting_started/your_first_plugin)!
