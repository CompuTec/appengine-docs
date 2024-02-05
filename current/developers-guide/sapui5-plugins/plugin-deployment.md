# Plugin Deployment

## Description

Preparing deployment package is straight forward. Release build content should be packed into zip. This zip can be later used to install plugin as described here: Configuration and Administration#Plugins.

### Creating Deployment package

1. Open your solution in Visual Studio.

![VS Solution Open](./media/plugin-deployment/vs-solution-open.webp)

2. Change configuration to Release or Release10 - this depends of target SAP version. (10 stands for SAP Business One 10 version).

![Change to Release](./media/plugin-deployment/change-to-release-10.webp)

3. Rebuild solution.

![Rebuild](./media/plugin-deployment/rebuild.webp)

4. Now we need to pack build content of Plugin Project. You can find path of your build in build output (or in your project properties - build - output path).

![Build](./media/plugin-deployment/build-result-path.webp)

5. Finally we just need to pack content of build into zip archive.

![Build Content](./media/plugin-deployment/build-content-explorer.webp)

6. Only created zip file is required to install plugin into AppEngine.

![Zip file](./media/plugin-deployment/zip-file.webp)
