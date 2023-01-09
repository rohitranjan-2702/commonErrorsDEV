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

### 2. `CORS` (Cross-Origin Resource Sharing) error, which comes when an application running on one port accesses application running on another port.

## Solution

We will be serving both react and Nodejs apps on the same port
add new scripts in `package.json` file.
```bash
"start-server": "node server/index.js",  
"start-app": "npm run build && npm run start-server"
```
So your `package.json` scripts section will look like this

![](https://miro.medium.com/max/700/1*sFnvqm3aRKd_L3uV4neldA.png)

Here in the  `start-app`  script, we are running  `npm run build`  script first and then  `npm run start-server`

So from the terminal execute the following command.
```javascript 
npm run start-app
```
This will create  `build`  folder with all of our react code and start the express server of  `server/index.js`  file so now both react and Nodejs app is accessible on the same  `3030`  port.

If you navigate to  `http://localhost:3030/`  , you will see that our application still works.

Include this in server.js :
```
const buildPath = path.join(__dirname, '..', 'build');
app.use(express.json());
app.use(express.static(buildPath));
```
## Screenshots




## Authors

- [@rohit](https://www.github.com/itzROHIT-coder)
- [@twitter](https://twitter.com/rohit_ranjan27)

