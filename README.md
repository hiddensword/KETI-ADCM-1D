# KETI-ADCM-1D


# 프로세서 모듈
- Odroid XU4


# Odroid 이미지
- Ubuntu 16.04 `ubuntu-16.04.3-4.14-mate-odroid-xu4-20171212.img`


# ROS 설치 관련 자료
- [오드로이드(ODROID) XU4 기반 ROS 설치 (20158-09-26)](http://daddynkidsmakers.blogspot.com/2015/09/odroid-xu4-ros.html)
  - Ubuntu 15.04
- [Using ODROID XU4 with Ubuntu 16 and ROS Kinetic](https://github.com/uzh-rpg/rpg_svo_example/issues/25)
  - SVO 2.0의 Wiki
- [Odroid Install](https://github.com/johnny-wang/odroid-install)
	- Install Ubuntu 16.04
	- Install ROS Kinetic
	- 본 Repository의 기본 자료


# ROS 버젼 및 설치
- ROS Kinetic
- [출처] https://github.com/johnny-wang/odroid-install
- http://wiki.ros.org/Installation/UbuntuARM

1. Set up sources.list
~~~
	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
~~~

2. Set up keys
~~~
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
~~~

3. Update
~~~
	sudo apt-get update
~~~

4. Install everything
~~~
	sudo apt-get install ros-kinetic-desktop-full
~~~

	- 이 단계에서 아래와 같은 에러 메시지를 받을 수 있음.
~~~
		E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
~~~
	- 16.04가 자동으로 upbrade를 check하기 때문임. disable하기 위해서 아래의 코드를 터미널에 입력하고, 재부팅.
~~~
		$ sudo systemctl disable apt-daily.service # disable run when system boot
		$ sudo systemctl disable apt-daily.timer   # disable timer run
~~~

5. Initialize rosdep
~~~
	sudo rosdep init
	rosdep update
~~~

6. Environment setup
~~~
	echo "source /opt/ros/lunar/setup.bash" >> ~/.bashrc
	source ~/.bashrc
~~~
