# tcp-socket-client
TCP Socket Client with Electron and Vue js

### create vue-cli project with name
vue create tcp-socket-client

### go into folder
cd tcp-socket-client

### install bootsrap 
yarn add bootstrap@next

### install and invoke the generator of vue-cli-plugin-electron-builder by running:
vue add electron-builder

### add lines into vue.config.js
module.exports = {
  pluginOptions: {
    electronBuilder: {
      nodeIntegration: true
    }
  }
}

### in background.js make shure that node is integrated 
function createWindow () {
  // Create the browser window.
  win = new BrowserWindow({ width: 800, height: 600, webPreferences: {
    // Use pluginOptions.nodeIntegration, leave this alone
    // See nklayman.github.io/vue-cli-plugin-electron-builder/guide/security.html#node-integration for more info
    nodeIntegration: process.env.ELECTRON_NODE_INTEGRATION
  } })

### run for development 
yarn electron:serve

### build app 
yarn electron:build
