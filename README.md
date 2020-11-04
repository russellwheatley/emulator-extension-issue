## Firebase emulator bug

I've copied this code from the `rtdb-limit-child-nodes` extension from this [extension's](https://github.com/firebase/extensions) repo [pull request](https://github.com/firebase/extensions/pull/482).



## Steps To Recreate

- you may have to change the project id in `functions/emulator/firebaserc` file to your own default project id.
- run `cd functions/ && npm i && npm run build` from root project directory.
- open a new terminal in root project directory  and run `cd functions/emulator && firebase emulators:start` (assuming you have `firebase-tools` installed globally).

Note the console output that indicates the cloud function has been successfully initialized:

```bash 
✔  functions[rtdblimit]: database function initialized.
```

- Kill the emulator process.
- change  line 43 of code in the `functions/src/index/ts` as indicated in the file.
- run `cd functions/emulator && firebase emulators:start` again from root project directory.

Note that the cloud function is not initialized as it does not know the database emulator is running:

```bash
i  functions[rtdblimit]: function ignored because the unknown emulator does not exist or is not running.
```
