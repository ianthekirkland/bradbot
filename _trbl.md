
## Summary  
###### Thursday, November 16, 2017  


Compile error related to use of *.ts in node_modules

```  
ERROR in ./node_modules/api-ai-javascript/index.ts  
```  


## Error  

```  
ERROR in ./node_modules/api-ai-javascript/index.ts  
Module build failed: Error: /Users/Ian/Dropbox/Development/Projects/angular-chatbot-fromScratch/chatbot/node_modules/api-ai-javascript/index.ts is not part of the compilation output. Please check the other error messages for details.  
    at AngularCompilerPlugin.getCompiledFile (/Users/Ian/Dropbox/Development/Projects/angular-chatbot-fromScratch/chatbot/node_modules/@ngtools/webpack/src/angular_compiler_plugin.js:629:23)  
    at plugin.done.then (/Users/Ian/Dropbox/Development/Projects/angular-chatbot-fromScratch/chatbot/node_modules/@ngtools/webpack/src/loader.js:467:39)  
    at process._tickCallback (internal/process/next_tick.js:109:7)  
    @ ./src/app/chat/chat.service.ts 12:0-48  
    @ ./src/app/chat/chat.module.ts  
    @ ./src/app/app.module.ts  
    @ ./src/main.ts  
    @ multi webpack-dev-server/client?http://0.0.0.0:0 ./src/main.ts  

webpack: Failed to compile.  
webpack: Compiling...  
Date: 2017-11-17T05:26:12.676Z  
Mac-Pro:chatbot Ian$ angular/cli --version  
sh: angular/cli: No such file or directory  
Mac-Pro:chatbot Ian$ ng -version  
The specified command -version is invalid. For available options, see `ng help`.  
Mac-Pro:chatbot Ian$ ng --version  
```  


## Solution  

@see  https://github.com/jf3096/json-typescript-mapper/issues/33  
@see  https://github.com/angular/angular-cli/issues/8284  

- Add this to 'chatbot/tsconfig.json':  

```  
"include": [  
    "src/**/*",  
    "node_modules/api-ai-javascript/index.ts"  
]
```  

- Add this to top of 'chatbot/node_modules/api-ai-javascript/.npmignore':  

```  
    *.ts  
    !*.d.ts  
```