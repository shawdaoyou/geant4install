# geant4的安装教程
1.下载需要的软件包和数据包 
下载root 
https://root.cern/install/all_releases 
![image](https://github.com/daoy939/geant4install/assets/65938631/0fa0ac9b-83bc-4e21-9626-72dff24ab0f6)

下载geant4 
https://geant4.web.cern.ch/download/all 
![image](https://github.com/daoy939/geant4install/assets/65938631/d3f9473e-bb78-4ab5-b410-1ea74296e6c8)
___
2.准备安装文件 
在\~目录下面创建一个geant4的文件夹 
将下载好的14个文件移动到这个文件夹下(~/geant4/) 
___
3.打开终端，执行以下命令 
ps:-j6换成自己电脑的核心数 
cd ~  && \  
sudo cp -r geant4/ /usr/local/  && \  
cd /usr/local/geant4/  && \  
sudo mv /usr/local/geant4/geant4*.tar.gz ..  && \  
cd ..  && \  
sudo tar -zxvf geant4*.tar.gz  && \  
sudo rm -rf geant4*.tar.gz  && \  
sudo apt install curl g++ libgl1-mesa-dev cmake libx11-dev libxext-dev libxtst-dev libxrender-dev libxmu-dev libxmuu-dev libhdf5-serial-dev hdf5-tools libexpat1 libexpat1-dev build-essential -y  && \  
sudo apt install qt5* -y  && \  
sudo mkdir geant4-install  && \  
sudo mkdir geant4-build &&\  
cd geant4-build  && \  
sudo cmake -DCMAKE_INSTALL_PREFIX=/usr/local/geant4-install -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_RAYTRACER_X11=ON -DGEANT4_USE_QT=ON -DGEANT4_BUILD_MULTITHREADED=ON /usr/local/geant4-v* && \  
sudo make -j6  && \  
sudo make install -j6  && \  
echo "source /usr/local/geant4-install/bin/geant4.sh" >> ~/.bashrc  && \  
cd /usr/local/geant4/  && \  
sudo mkdir -p /usr/local/geant4-install/share/Geant4/data  && \  
sudo mv G4*.tar.gz /usr/local/geant4-install/share/Geant4/data  && \  
cd /usr/local/geant4-install/share/Geant4/data  && \  
sudo ls *.tar.gz | sudo xargs -n1 tar xzvf  && \  
sudo rm -rf G4*.tar.gz  && \  
cd /usr/local/geant4/  && \  
sudo tar -zxvf root*.tar.gz  && \  
sudo mv root /usr/local/  && \  
sudo rm -rf root*.tar.gz  && \  
sudo rm -rf /usr/local/geant4/ && \  
echo "source /usr/local/root/bin/thisroot.sh" >> ~/.bashrc  && \  
source ~/.bashrc  && \  
mkdir ~/geant4_ws && \  
cd ~/geant4_ws  && \  
cp -r /usr/local/geant4-install/share/Geant4/examples ~/geant4_ws && \  
cp -r  \~/geant4_ws/examples/basic/B1 ~/geant4_ws  
___
4.打开vscode 
安装好C++插件 
打开文件夹，选择~/geant4_ws/B1 
按快捷键Ctrl+Shift+P调出命令面板，输入C/C++，选择“Edit Configurations(UI)”进入配置 
在包含路径项添加/usr/local/geant4-install/lib 
![image](https://github.com/daoy939/geant4install/assets/65938631/bc9bf449-bd0b-4a0a-8946-ea388352ab91)
___
建议将ubuntu的默认sh改为bash 
(从ubuntu 6.10开始，默认使用dash) 
在终端输入
sudo dpkg-reconfigure dash 
然后选择No
