# Multi Stage Multi Agent

</br>

Set up a multi stage jenkins pipeline where each stage is run on a unique agent. This is a very useful approach when you have multi language application
or application that has conflicting dependencies.

</br>

## Steps involved in it are pretty much similar to the previous one.

</br>

 - You have to just replace the Script path my this folder name, as shown below.

</br >

![f15](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/9dd926ad-d06d-4ea3-851a-8456676bcacd)

</br >
 
 - Run the following docker command to check whether the container has been build or not. You can see that once the execution is 
   done the Jenkins application automatically deletes the container.

</br >

```
docker ps
```

</br >

![f16](https://github.com/SubodhBagde/Jenkins-Demo-Pipeline/assets/136182792/bc419cf9-9e28-4b41-b9b4-b5afdb1ed15f)

</br >

The Multi Stage Multi Agent process is successful.
