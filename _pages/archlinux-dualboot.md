---
layout: post
title: "듀얼부팅으로 아치 리눅스 설치하기 (with KDE Plasma)"
featured-img: archlinux-dualboot.jpg
---

# .iso 파일 다운로드

[여기를 눌러서](https://archlinux.org/) 아치 리눅스 홈페이지로 이동하면 오른쪽 위에 `Download`라는 문구가 보일거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/0.png)

<br />
거기로 들어가셔서 토렌트를 통해 받으시거나

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/1.png)

<br />
더 아래로 내리면 바로 파일 다운로드가 가능한 미러들이 있을텐데

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/2.png)

<br />
한국 미러들도 있으니, (일부 미러는 작동하지 않을 수도 있어요)

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/3.png)

<br />
적당히 골라서 받으시면 되는거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/4.png)

***
<br />

# 윈도우 파티션 용량 줄이기

윈도우가 설치되어 있는 파티션의 공간을 줄일거에요. 일단 여기서는 전 `16GiB`를 줄였어요.
줄이는 방법은 [여기를](./windows-disk-partition) 참고하시면 되는거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/5.png)

***
<br />

# 아치 리눅스로 부팅하기

`rufus`나 `ventoy` 등을 통해 부팅 USB를 만들어서, 해당 USB를 통해 아치 리눅스로 부팅하시면 이런 화면이 나올거에요.
그냥 엔터치고 기다리시면,

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/6.png)

<br />
이런식으로 아치 리눅스가 켜질거에요. 이제 일일이 명령어를 입력해서 아치 리눅스를 설치해볼거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/7.png)

***
<br />

# 인터넷 연결하기 (와이파이)

유선 인터넷을 사용하신다면 이미 인터넷 연결은 되어있겠지만, 와이파이를 통해 무선인터넷을 사용하시려는 경우에는 명령어를 통해 직접 연결해줘야 해요. `iwctl`를 사용하시면 되는거에요.

```
# iwctl
```

<br />
`iwctl`를 실행하셨다면, 다음 명령어들을 통해 와이파이에 연결하시면 되는거에요.
```
[iwctl] device list   //네트워크 인터페이스 찾기 (대충 컴퓨터에 들어있는 와이파이 잡는 부품 찾기)
[iwctl] station {interface} scan   //해당 인터페이스를 통해 주변 와이파이 검색
[iwctl] station {interface} get-networks   //검색된 와이파이 목록 출력
[iwctl] station {interface} connect "Wi-Fi Name"   //해당 와이파이로 연결
```

<br />
와이파이에 비밀번호가 걸려있다면, 비밀번호도 입력하시고 엔터치시면 되는거에요. 다 끝났으면 `exit`를 입력해서 `iwctl`에서 나와주세요.
```
[iwctl] exit
```

<br />
대충 이거랑 비슷한 모습을 볼 수 있을거에요. 검색 버튼 누르고, 와이파이 목록을 직접 누르던걸 그냥 다 명령어로 입력한다고 보시면 되는거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/8.jpg)

<br />
`ping` 요청을 보냈을 때 잘 작동하는 것을 보니, 인터넷에 연결된 듯 해요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/9.png)


***
<br />
# 리눅스를 설치할 파티션 만들기

`lsblk` 명령어를 입력하면 이런식으로 파티션 목록이 뜰텐데, 여기서 아까 파티션을 줄였던 디스크를 찾아주세요. 전 가만 보아하니 `nvme0n1`이 아까 용량을 줄인 디스크인 듯 해요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/10.png)

<br />
다음 명령어를 입력해서 해당 디스크를 대상으로 `cfdisk` 실행
```
# cfdisk {disk}   //필자의 경우, cfdisk /dev/nvme0n1
```

<br />
아까 윈도우에서 줄였을 때 이런 모습이였는데

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/11.png)

<br />
똑같이 생긴걸 볼 수 있어요. 그냥 글자로만 적혀있는거 말곤 똑같아요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/12.png)

<br />
`상/하 방향키`를 통해 아까 줄였던 빈 공간을 선택한 뒤에, `좌/우 방향키`를 통해 `New`를 선택하고 엔터

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/13.png)

<br />
용량은 알아서 최대치로 입력되어 있을 것이니 엔터

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/14.png)

<br />
그럼 아까 그 빈 공간에 `Linux FileSystem`이라고 적혀있는걸 볼 수 있는데, 아칙 수정사항이 반영된건 아니니 `Write` 선택 후 엔터

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/15.png)

<br />
진짜로 바꿀꺼냐고 물어보는거에요. 빈 공간을 잘못 골랐으면 원래 컴퓨터에 있던게 몽땅 다 지워지고 웬만하면 복원도 불가능할 것이니 다시 한 번 확인해보세요. `yes`를 입력하신 뒤에 엔터치시면 수정사항이 반영될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/16.png)

<br />
다 끝났으면 `Quit` 선택 후 엔터를 쳐서 `cfdisk` 종료

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/17.png)

<br />
`lsblk`를 또 입력해서 확인해보니 맨 아레에 파티션이 생겼어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/18.png)

<br />
`mkfs.ext4` 명령어를 통해 방금 만든 파티션을 `Ext4`라는 파일 시스템으로 포멧싴주세요.
```
# mkfs.ext4 {리눅스를 설치할 파티션}   //필자의 경우, mkfs.ext4 /dev/nvme0n1p4
// 아까와는 달리 뒤에 p어쩌고 붙여야 해요.
// 실수로 빼먹으면 파티션이 아니라 다스크 전체를 포멧하는거라, 원래 있던 파일이 다 지워질거고, 복구도 사실상 불가능할거에요.
```

<br />
그리고 다음 명령어 입력. `리눅스를 설치할 파티션`과 `EFI 파티션`을 마운트하는건데, 여기서도 잘못 마운트하면 이상하게 작동할 수도 있어요.
```
# mount /dev/{리눅스를 설치할 파티션} /mnt
# mkdir -p /mnt/boot/efi
# mount /dev/{EFI 파티션} /mnt/boot
```

<br />
아무튼 제가 명령어 실행했던 모습

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/19.png)

***
<br />

# 아치 리눅스 설치

다음 명령어를 입력해서 아치 리눅스 및 필요한 것들을 설치해주세요.
```
# pacstrap /mnt base base-devel linux linux-firmware vim networkmanager
```

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/20.png)

***
<br />

# 설치 후 기타 작업

설치가 끝났으면 `fstab`을 생성해주세요. 그리고 `arch-chroot` 명령어를 통해 방금 설치한 아치 리눅스에 진입 비슷한걸 할거에요. 진입한 상태에서는 앞에 뜨는게 뭔가 바뀌었을거에요.
```
# genfstab -U /mnt >> /mnt/etc/fstab
# arch-chroot /mnt
```
![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/21.png)

<br />
재부팅한 이후에 인터넷을 사용할 수 있도록 `NetworkManager`를 `enable`헤주시고, `root` 계정의 비밀번호 설정 및 새로운 사용자 계정 추가 등을 해주세요.
```
# systemctl enable NetworkManager
# passwd root   //이 명령어 입력 후 루트 계정의 비밀번호로 사용할 내용 입력
# useradd {추가할 계정 이름}
# passwd {추가한 계정 이름}   //이 명령어 입력 후 루트 계정의 비밀번호로 사용할 내용 입력
# mkdir /home/{추가한 계정 이름}   //미리 폴더 안말들어두면 오류떠요
# chmod 777 /home/{추가한 계정 이름}  //만들기만 하고 권한 부여 안해줘도 오류떠요
```

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/22.png)

***
<br />

# 부트로더 설치

`컴퓨터 전원 On -> 부트로더 실행 -> 운영체제 부팅` 순서인데, 아직은 `운영체제(리눅스)`만 설치한 상태에요. 그러니, 리눅스용 부트로더인 `grub`를 설치할거에요.
```
# pacman -S grub efibootmgr dosfstools mtools os-prober
# grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id={부트 메뉴에서 보일 이름}
# grub-mkconfig -o /boot/grub/grub.cfg
```

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/23.png)

<br />
어라 리눅스만 찾고 윈도우는 찾지 못한 것 같지만, 이건 나중에 해결할거에요.

***
<br />

# KDE Plasma 설치 (데스크톱 환경 설치)

지금 검은 화면에 흰 글자로만 쓰고 있는데, 사실 리눅스만 설치한거라서 재부팅해도 이 환경 그대로일거에요. 바탕화면이 있고 마우스 움직이면 커서도 따라 움직이도, 아이콘들도 있는 데스크톱 환경(GUI 환경)도 따로 설치해주어야 해요. 일단 전 `KDE`에서 만든 `Plasma`를 설치할거에요.

`Plasma` 말고도, `GNOME`, `Xfce`, `MATE`, `Cinnamon`, `LXDE`, `Deepin` 등 많이 있으니, 다른 것을 쓰시고 싶으시다면 해당 환경을 설치하는 방법을 찾아보세요. 근데, 개인적으로 생긴건 `Plasma`가 깔끔하고 이쁘긴 해요.

아무튼 다음 명령어를 입력하면 `KDE Plasma`와 필요한 것들이 설치될거에요. 뭐 고르라면서 자꾸 물어볼텐데 그냥 다 엔터치셔도 됩니당.
```
# pacman -S plasma plasma-wayland-session xorg-server
```
![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/24.png)

<br />
용량이 좀 많아요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/25.png)

<br />
설치가 끝났다면 `sddm`을 enable`시키고 `chroot`에서 나간 뒤에 재부팅
```
# systemctl enable sddm
# exit
# reboot
```

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/26.png)

***
<br />

# 같이 설치된 윈도우 찾아오기 등

`grub`가 리눅스는 잘 찾았는데, 같이 깔려있는 윈도우는 못찾고 있어요. 일단 저 상태에서 엔터를 치시거나 좀 기다리시면 리눅스로 켜질건데

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/27.png)

<br />
어엄... 사용자 계정 로그인 화면이 너무 몬생긴 듯 해요. 리눅스가 켜지면 `sddm`이 켜지고 거기서 로그인을 하면 `Plasma` 환경으로 들어가는 방식이에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/28.jpg)

<br />
계정 선택 후 비밀번호를 입력하시면 `Plasma` 환경이 설치된 리눅스가 나올거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/29.jpg)

<br />
일단 몬생긴 로그인 화면 디자인은 설정에서 바꿀 수 있어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/30.jpg)

<br />
아무튼 터미널을 열려고 했는데 어라 터미널이 없어요. `KDE Plasma`의 터미널은 `Konsole`인데, 이게 없네;;

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/31.jpg)

<br />
`Ctrl + Alt + F2` 같은 명령어를 통해, 아무튼 마지막에 F1, F2, F3 막 눌러보다가 보면 이런 CLI 화면으로 다시 나올 수 있어요.
root 계정으로 로그인한 뒤에 다음 명령어를 입력해서 `konsole` 설치 후 재부팅
```
pacman -S konsole
```
![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/32.png)

<br />
아무튼 재부팅했더니 konsole이 이제 잘 열려요. 아직 사용자 추가만 하고 `sudoer`에는 해당 사용자를 넣지 않은지라 일단 root 계정으로 들어왔어요.

로그인 화면에 root 계정이 보이지도 않고 직접 입력 같은 것도 안보일텐데, 그건 일단 아무 계정으로 로그인한 뒤에 설정 들어가서 로그인 화면 디자인 바꾸시면 될거에요.

아무튼 `/usr/bin/grub-mkconfig` 파일을 열고,
![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/33.png)

<br />
`GRUB_DISABLE_OS_PROBER="true"`라고 써있는거에서 `true`를 `false`로 바꿔주세요.

방향키 등을 통해 해당 위치로 커서 이동 뒤 `a`를 눌러서 수정 모드로 들어가서 수정하신 뒤에, `ESC`키 눌러서 수정 모드에서 나오시고 `:wq` 입력하고 엔터치시면 저장 및 닫기가 될거에요.
```
GRUB_DISABLE_OS_PROBER="false"
```
![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/34.png)

<br />
`grub-mkconfig -o /boot/grub/grub.cfg`를 다시 입력해주면 이런식으로 리눅도 찾고 윈도우도 잘 찾아요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/35.png)

<br />
이제 재부팅을 하시면 이렇게 `리눅스(Arch Linux)`와 `윈도우(Windows Boot Manager)`가 모두 있는 것을 볼 수 있어요.
`상/하 방향키`를 통해 리눅스 또는 윈도우를 선택하시고 엔터치시면 리눅스 또는 윈도우로 켜질거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/36.png)

<br />
아무튼 전 이렇게 커스터마이징을 해놓았어요. 히히 이뿌덩

![image]({{site.url}}{{site.baseurl}}/assets/images/archlinux-dualboot/37.jpg)

