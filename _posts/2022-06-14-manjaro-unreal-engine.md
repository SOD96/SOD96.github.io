---
title: Compiling Unreal Engine 5 on Arch Linux (Manjaro)
date: 2022-06-13 13:24:00 +0000
categories: [development]
tags: 
- C++
- CPlusPlus
- Unreal engine
- Unreal
- Game Development
- Manjaro
- Arch Linux
- Unreal Engine Arch Installation
- 5.17.9-1-MANJARO
- Unreal Engine Manjaro Setup
- Unreal Engine Errors on Setup
- Unreal Engine Errors on Start
---

# Setting up Unreal Engine on Manjaro

I decided to take the plunge back into Unreal Engine. I was aware it could compile for Linux so figured I'd give it a go. First and foremost, you should follow the installation guide as much as possible, you can find it here: https://github.com/EpicGames/UnrealEngine/blob/release/Engine/Build/BatchFiles/Linux/README.md


These are the commands that I did...

```
git clone git@github.com:EpicGames/UnrealEngine.git  
sudo pacman -S dotnet-sdk 
sudo pacman -S yay
yay -S libicu50 --noconfirm 
cd UnrealEngine
./Setup.sh
sudo mkdir /usr/local/ssl
sudo ln -s /etc/ssl/certs /usr/local/ssl
sudo mkdir /usr/lib/ssl
sudo ln -s /etc/ssl/certs /usr/lib/ssl
./GenerateProjectFiles.sh
```

If you follow the above, you should pass any installation issues that I got, for reference I've attached the errors I was getting during installation so hopefully this comes up a bit better on the search results. Should save you a few hours googling down many rabbit holes of OpenSSL issues and .Net

## My Errors


First we had **Unable to load the service index for source https://api.nuget.org/v3/**
```
~/code/unreal/UnrealEngine ./GenerateProjectFiles.

Attempting to set up UE pretty printers for gdb (existing UEPrinters.py, if any, will be overwritten)...
        updated UEPrinters.py
        found necessary entries in ~/.gdbinit file, not changing it.

Setting up Unreal Engine 5 project files...

Setting up bundled DotNet SDK
/home/sean/code/unreal/UnrealEngine/Engine/Binaries/ThirdParty/DotNet/Linux/sdk/3.1.401/NuGet.targets(255,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/sean/code/unreal/UnrealEngine/Engine/Source/Programs/UnrealBuildTool/UnrealBuildTool.csproj]
/home/sean/code/unreal/UnrealEngine/Engine/Binaries/ThirdParty/DotNet/Linux/sdk/3.1.401/NuGet.targets(255,5): error :   The SSL connection could not be established, see inner exception. [/home/sean/code/unreal/UnrealEngine/Engine/Source/Programs/UnrealBuildTool/UnrealBuildTool.csproj]
/home/sean/code/unreal/UnrealEngine/Engine/Binaries/ThirdParty/DotNet/Linux/sdk/3.1.401/NuGet.targets(255,5): error :   The remote certificate is invalid according to the validation procedure. [/home/sean/code/unreal/UnrealEngine/Engine/Source/Programs/UnrealBuildTool/UnrealBuildTool.csproj]
```

During setup I also had a few prompts come up with unreadable characters. I selected the first box because the second means cancel. I'm not sure what this does, but nothing bad has happened.... yet, queue a blog post of me formatting next week.

## My Setup
```
Operating System: Manjaro Linux
KDE Plasma Version: 5.24.5
KDE Frameworks Version: 5.94.0
Qt Version: 5.15.4
Kernel Version: 5.17.9-1-MANJARO (64-bit)
Graphics Platform: X11
Processors: 24 × AMD Ryzen 9 3900X 12-Core Processor
Memory: 31.3 GiB of RAM
Graphics Processor: NVIDIA GeForce RTX 2080 Ti/PCIe/SSE2
```
## Sources

https://github.com/EpicGames/UnrealEngine/blob/release/Engine/Build/BatchFiles/Linux/README.md
https://forums.unrealengine.com/t/error-compiling-unreal-engine-on-arch-linux/549637/11
