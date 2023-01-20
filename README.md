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

```
var schema = new Schema({
  name:    String,
  binary:  Buffer,
  living:  Boolean,
  updated: { type: Date, default: Date.now },
  age:     { type: Number, min: 18, max: 65 },
  mixed:   Schema.Types.Mixed,
  _someId: Schema.Types.ObjectId,
  decimal: Schema.Types.Decimal128,
  array: [],
  ofString: [String],
  ofNumber: [Number],
  ofDates: [Date],
  ofBuffer: [Buffer],
  ofBoolean: [Boolean],
  ofMixed: [Schema.Types.Mixed],
  ofObjectId: [Schema.Types.ObjectId],
  ofArrays: [[]],
  ofArrayOfNumbers: [[Number]],
  nested: {
    stuff: { type: String, lowercase: true, trim: true }
  },
  map: Map,
  mapOfString: {
    type: Map,
    of: String
  }
})

// example use

var Thing = mongoose.model('Thing', schema);

var m = new Thing;
m.name = 'Statue of Liberty';
m.age = 125;
m.updated = new Date;
m.binary = Buffer.alloc(0);
m.living = false;
m.mixed = { any: { thing: 'i want' } };
m.markModified('mixed');
m._someId = new mongoose.Types.ObjectId;
m.array.push(1);
m.ofString.push("strings!");
m.ofNumber.unshift(1,2,3,4);
m.ofDates.addToSet(new Date);
m.ofBuffer.pop();
m.ofMixed = [1, [], 'three', { four: 5 }];
m.nested.stuff = 'good';
m.map = new Map([['key', 'value']]);
m.save(callback);
```
## Screenshots




## Authors

- [@rohit](https://www.github.com/itzROHIT-coder)
- [@twitter](https://twitter.com/rohit_ranjan27)

