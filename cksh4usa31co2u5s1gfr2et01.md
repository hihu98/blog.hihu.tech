## Using Mactype on Chromium-based browsers

One of many reasons that I love macOS and Linux is that their font-render mechanic is so smooth. I do not know why Microsoft, with their 30s year-old operating system, can easily accept that fonts in Windows is so ugly. 

That's why I use [Mactype](https://github.com/snowie2000/mactype) on almost every Windows machine I have. This software provides another way to render font on Windows OS, and they are such perfect with me. However, Chromium-based browsers do not follow the solution. I should do a trick, add a flag to browser command. 

```
-disable-features=RendererCodeIntegrity
```

Add this code to browser shortcut or open command, like this: 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629269059413/TAPfFh1An.png)

It works!



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629269164818/VtLjb9nM1.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629269105635/DqNtVTssz.png)

I don't know which one you like more, but it suite for me. By the way, I use CleanDark default profile for Mactype. 
