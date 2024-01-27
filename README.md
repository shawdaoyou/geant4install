# geant4的安装教程
1.下载需要的软件包和数据包  
下载root  
https://root.cern/install/all_releases  
![image](https://github.com/daoy939/geant4install/assets/65938631/6734d76d-83d0-4f95-adeb-d6f2b899c70a)


下载geant4  
https://geant4.web.cern.ch/download/all  
![image](https://github.com/daoy939/geant4install/assets/65938631/92519af2-9b90-452b-8924-a4cf6b381997)

___
2.准备安装文件  
在\~目录下面创建一个geant4的文件夹  
将下载好的14个压缩文件移动到这个文件夹下(\~/geant4/)  
___
3.打开终端，执行以下命令  
ps:-j6换成自己电脑的核心数,先复制到记事本修改  
cd \~  && \  
sudo cp -r geant4/ /usr/local/  && \  
cd /usr/local/geant4/  && \  
sudo mv /usr/local/geant4/geant4\*.tar.gz ..  && \  
cd ..  && \  
sudo tar -zxvf geant4\*.tar.gz  && \  
sudo rm -rf geant4\*.tar.gz  && \  
sudo apt install curl g++ libgl1-mesa-dev cmake libx11-dev libxext-dev libxtst-dev libxrender-dev libxmu-dev libxmuu-dev libhdf5-serial-dev hdf5-tools libexpat1 libexpat1-dev build-essential -y  && \  
sudo apt install qt5\* -y  && \  
sudo mkdir geant4-install  && \  
sudo mkdir geant4-build &&\  
cd geant4-build  && \  
sudo cmake -DCMAKE_INSTALL_PREFIX=/usr/local/geant4-install -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_RAYTRACER_X11=ON -DGEANT4_USE_QT=ON -DGEANT4_BUILD_MULTITHREADED=ON /usr/local/geant4-v* && \  
sudo make -j6  && \  
sudo make install -j6  && \  
echo "source /usr/local/geant4-install/bin/geant4.sh" >> \~/.bashrc  && \  
cd /usr/local/geant4/  && \  
sudo mkdir -p /usr/local/geant4-install/share/Geant4/data  && \  
sudo mv G4\*.tar.gz /usr/local/geant4-install/share/Geant4/data  && \  
cd /usr/local/geant4-install/share/Geant4/data  && \  
sudo ls \*.tar.gz | sudo xargs -n1 tar xzvf  && \  
sudo rm -rf G4\*.tar.gz  && \  
cd /usr/local/geant4/  && \  
sudo tar -zxvf root\*.tar.gz  && \  
sudo mv root /usr/local/  && \  
sudo rm -rf root\*.tar.gz  && \  
sudo rm -rf /usr/local/geant4/ && \  
echo "source /usr/local/root/bin/thisroot.sh" >> \~/.bashrc  && \  
source \~/.bashrc  && \  
mkdir \~/geant4_ws && \  
cd \~/geant4_ws  && \  
cp -r /usr/local/geant4-install/share/Geant4/examples \~/geant4_ws
___
4.验证geant4
cp -r  \~/geant4_ws/examples/basic/B1 \~/geant4_ws   
cd \~/geant4_ws/B1  
mkdir build   
cd build   
cmake ..   
make  
./exampleB1
