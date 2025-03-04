

### 1. Repository Creation in Gitea
- I created a new repository in Gitea called **laboratorio 3 ** without an initial README.
- I cloned the repository to my local machine using:
  ```bash
  git@gitea.com:
  ```


### 2. Configure Environment Branches

Using the terminal:

#### Create the following branches to represent the environments and protect them:

**`development` : For active feature development**  

  ```bash
  git branch development 
  ```

![](./images/1.png)

 ```bash
  git push -u origin  development 
  ```


![](./images/2.png)


**`staging` : For testing and pre-production.**    
  
  ```bash
  git branch staging 
  ```

![](./images/3.png)

 ```bash
  git push -u origin stating 
  ```


![](./images/4.png)


**`production` : For the stable, live version.**  

  ```bash
  git branch production 
  ```

![](./images/5.png)

 ```bash
  git push -u origin  production 
  ```

![](./images/6.png)



**Protect the `staging` and `production` branches.**  

For the part about protecting branches, I did it from the web interface first:

I put the name of the branch `stating`:

- In the push part I left it as disable push

![](./images/7.png)


- Then I left the option `disable forced push`

![](./images/8.png)

- For the merge part I left `enable merge` and `block merge if pull request is out of date`

![](./images/9.png)

I repeated these same steps for the `production` branch.


### 3. Develop Features

Using the terminal:

**Switch to the `development` branch.**  

 ```bash
 git checkout development
  ```
**Create a `feature` branch for `implementing` a homepage .**  

 ```bash
 git checkout -b feature/homepage
  ```

![](./images/11.png)

Implement the following changes:

- Create a file `index.html` with a basic homepage structure. 

```bash
 touch index.html
 code index.html
  ```

![](./images/12.png)

- Structure file `index.html`

![](./images/13.png)

- Create a file `styles.css` for the homepage styling.

![](./images/14.png)

Structure `style.css`

![](./images/15.png)


- Add a script `main.js` to log "Hello, World!" to the browser console.

![](./images/16.png)

Structure `main.js`

![](./images/17.png)


**Make three separate commits:**  


- **Commit 1: `feat(GIT 0001 Add basic HTML structure for the homepage.`**  

![](./images/18.png)

- **Commit 2 `feat(GIT 0002 Add CSS styling for the homepage.`**  

![](./images/19.png)

- **Commit 3: `feat(GIT 0003 Add JavaScript functionality to log a message.`**

![](./images/20.png)

#### Push your changes to the feature branch.

```bash
 git push origin feature/homepage
  ```
![](./images/21.png)


### 4. Merge Changes into Development

Using the Web UI:

**Create the Pull Request using all the good practices reviewed in class.**  

- First we show the branches to merge and where we will get those changes we go from `feature/homepage` to the `development` branch

![](./images/22.png)

- We create our PR with the structure seen in class

![](./images/23.png)

![](./images/24.png)


**Merge the changes into `development`** 

- The merge that was made to our `development` branch is shown

![](./images/25.png)

- We download the changes to the local repository in the `development` branch

 ```bash
 git pull origin development
  ```
![](./images/26.png)


**Deleted branch from the remote and local repositories.**

*local:*
 ```bash
 git branch -d feature/homepage
  ```

*remote:*
 ```bash
 git push origin --delete feature/homepage 
  ```

![](./images/27.png)


### 5. Promote Changes to Staging

Using the Web UI

**Once testing in `development` is complete, create a Pull Request to merge the changes into `staging` also using the good practices.** 

- We make the PR from the `development` branch to the `stating` branch.

![](./images/28.png)

- We create our PR with the structure seen in class


![](./images/29.png)

![](./images/30.png)

- We download the changes to the local repository in the `stating` branch

![](./images/31.png)


### 6. Deploy Changesa to Production

Using the Web UI:

**Once testing in `staging` is complete, create a PR to merge the changes into `production`**


![](./images/32.png)

**Merge the changes into production.**

- We create our PR with the structure seen in class


![](./images/33.png)

Using the terminal:


- **Tag the release in the `production` branch.**


```bash
 git tag -a v1.0.0 -m "First release: Initial homepage release" 
  ```

![](./images/34.png)

- We show the tag created in the web UI

![](./images/35.png)


### 7. Handle a Hotfix

Using the terminal:

**Simulate a critical issue in production:**

To simulate an error in the production branch I first created a new branch:

- Create new branch `feature/brokenJs`

```bash
 git checkout -b feature/brokenJs 
  ```

![](./images/36.png)

- Then delete the semicolon that was in the `console.log` from the `main.js` file

- Identify a bug in `main.js`

![](./images/37.png)

We simulate that we sent our file remotely without realizing that it is misspelled using the commands:

```bash
git add
git commit
git push
  ```
 
![](./images/38.png)

- Accepted changes to merge `brokenJs` branches into `production`

![](./images/39.png)
`
![](./images/40.png)

**Create a `hotfix` branch from `production` .**


We download the changes and leave everything ready, realizing that there are errors in the js document

- Implement the fix.

- We create the `hotfix/js-error` branch

```bash
git checkout -b hotfix/js-error
  ```

![](./images/41.png)

- We fix the document and put the missing semicolon in it

![](./images/42.png)

- We push the `hotfix/js-error` branch

![](./images/43.png)


**Push the hotfix branch and create the PR to merge it into `production` .**

- We create the PR to send it to the `production` branch

![](./images/44.png)


**Merge the hotfix into `production` to deploy the fix, then promote it to `staging` and `development`.**

- We moved from `production` to `stating` with the new arrangement.

![](./images/45.png)

- We moved from `stating` to `development` with the final fixes to have all branches updated and without errors.

![](./images/46.png)





