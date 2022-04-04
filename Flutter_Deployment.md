## Deployment Flutter Web to Firebase

`Flutter` `Firebase`

- [ ] Create Firebase Project ( Don't Enable Google Analytics )

- [ ] Install Firebase-tools CLI (npm install -g firebase-tools)

- [ ] Initialize Firebase hosting
  
  ```js
  firebase login
  ```

- [ ] Run the below command from your root directory Flutter project
  
  ```
  firebase init
  ```

- [ ] Use **build/web** as your public directory
  
  ![](https://miro.medium.com/max/875/0*mYMsKK4g65KGh71f) 

Note: After this step, 2 new files are created (`.firebaserc` and `firebase.json`) in your root directory. Check and make sure they are there. If not, check for errors in the `firebase init` step and retry.

- [ ] Build and Deploy
  
  ```
  // Building flutter in (HTML & JavaScript)
  flutter build web --no-sound-null-safety 
  
  // Deployment 
  firebase deploy
  ```
