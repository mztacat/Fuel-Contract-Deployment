

--------------------------------


# Deploying a Contract on Fuel Network 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/79098f5b-4d5c-48a5-9eda-8b39b1cccde6)



##Install Dependencies  ---- 

```
sudo apt update
sudo apt upgrade -y
sudo apt-get install curl screen -y 
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/f9fb26d5-3d76-4349-855a-3fba14179514)


## Installing RUST 

```
curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustc --version
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/5aecb6a0-996e-428f-b827-2070678725aa)

```
rustup install stable
rustup update stable
rustup default stable
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/f78242c5-aac1-4513-af97-08c48dc79d5a)



## Install GIT 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/c271feba-3c9a-43dd-903f-6a68ad3d69e8)

```
sudo apt install git -y 
```


## Install Fuel Toolchain 

![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/a83a1f30-0333-4414-b6f4-c6f79793ac78)

```
curl https://install.fuel.network | sh
```

### press ```y``` then enter
 ![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/66a2c343-00ba-41ec-a08f-006866b1a0db)



 ### Setting PATH 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/1581ad4f-f1cb-4303-a037-b9579e6f087d)

```
source /root/.bashrc
```


### Setting ```FUELUP```

```
fuelup toolchain install latest
fuelup self update
fuelup update && fuelup default latest
```




## Creating PROJECT 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/af5b6c9c-f515-499a-a700-5f44e387833b)

```
mkdir fuel-project && cd fuel-project
forc new counter-contract
```



### Editing Contract 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/cba9e0b7-ecdf-401c-80ad-80c6f746c543)


```
nano counter-contract/src/main.sw
```

Clear/delete everything and paste below ```code```

```
contract;
 
storage {
    counter: u64 = 0,
}
 
abi Counter {
    #[storage(read, write)]
    fn increment();
 
    #[storage(read)]
    fn count() -> u64;
}
 
impl Counter for Contract {
    #[storage(read)]
    fn count() -> u64 {
        storage.counter.read()
    }
 
    #[storage(read, write)]
    fn increment() {
        let incremented = storage.counter.read() + 1;
        storage.counter.write(incremented);
    }
}
```


### Save and exit with  ```Ctrl X + y ```  and click ``` ENTER ``` 

--------------------------------------




## Build Contract 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/af8b7100-fa86-4177-9907-2575cd9abbf8)

```
cd counter-contract
forc build 
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/777ae627-7101-4ec0-8f3c-804f2c5c5e7d)






## Deploying Contract 
Remember, you will need your FUEL wallet here, i will be importing mine, if you don't have wallet, [Install from here](https://wallet.fuel.network/docs/install/)

![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/3d2e1430-d731-45c5-a74d-a391cc0bf60e)



### Importing wallet 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/468fac6b-3b48-4723-980a-606ae58b5427)


```
forc wallet import 
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/bb4f2b0d-533a-400c-9b09-8dba98bf8a72)


### and copy and paste on terminal
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/5841f34b-2476-4116-9e00-cebdecad08fb)

### Note:  ``` password are always invincible```

----------------


### Create Account 

```
forc wallet account new
```
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/33913d6b-2030-4c5f-896d-79e3ee6b32f8)

### Import account and input password 



### Check Address 

```
forc wallet accounts
```


---------

### Deploy Contract 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/8e5842f2-5b77-4c07-ac19-7ca689384ec6)

```
forc deploy --testnet 
```

### Enter ```0``` as Index and click ```y``` 
![image](https://github.com/mztacat/Fuel-Contract-Deployment/assets/31314340/f30a2bdc-365a-475f-a180-d41776a7f0ae)

# CONTRACT DEPLOYED 
----------


# EXPLORER 
[FUEL EXPLORER](https://app.fuel.network/) 

-------------











