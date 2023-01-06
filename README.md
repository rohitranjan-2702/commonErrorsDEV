# commonErrorsDEV
Solutions to some common issue/errors that developers face.


### 1. Running 'vercel' command after installing vercel 'npm i -g vercel'

ERROR:

vercel : File C:\Users\user\AppData\Roaming\npm\vercel.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see     
about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.


## Solution

 run the command like this

```bash
  Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Now you are good to go!

[Why this happens?]()
## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## Authors

- [@rohit](https://www.github.com/itzROHIT-coder)

