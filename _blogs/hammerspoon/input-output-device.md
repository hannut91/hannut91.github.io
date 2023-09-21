---
title: 해머스푼으로 입출력장치를 편하게 바꾸자
subTitle:
category:
tags:
createdat: 2023-09-21 14:05:00
updatedat: 2023-09-21 23:36:59
---

![](/images/hammerspoon/input-output.gif)

맥에 다른 스피커나 헤드폰이 연결되어 있는 경우처럼 여러개의 입출력 장치가 있는
경우, 상황에따라 변경하려면 시스템 설정 -> 사운드로 가서 변경해야 합니다. 매우 귀찮은 일을
단축키 한 번으로 변경할 수 있도록 해보겠습니다.  

필요한 것은 해머스푼이 필요한데요. 해머스푼은 맥에서 여러가지 자동화를 할 수 있는 도구입니다. 스크립트를 작성해서 내가 원하는 기능을 하도록 만들 수 있는 도구입니다. 

## 해머스푼 설치

homebrew로 설치합니다.

```bash
$ brew install --cask hammerspoon
```

## 설정 파일 추가하기

![](/images/hammerspoon/open-config.png)

해머스푼을 실행하고 화면 상단에 해머스푼 아이콘을 클릭하여 `Open Config`를
클릭합니다. 그러면 편집기로 `init.lua`파일이 열리는데 여기에 다음 스크립트를 추가합니다.

```lua
function change_output_device() 
  local currentOutputDevice = hs.audiodevice.defaultOutputDevice()
  local devices = hs.audiodevice.allOutputDevices()

  local index = hs.fnutils.indexOf(devices, currentOutputDevice)

  local device
  
  while true do
    device = devices[(index % #devices) + 1]
    if device == nil then
      index = index + 1
    else
      break
    end
  end

  device:setDefaultOutputDevice()
  hs.alert(device:name())
end

function change_input_device() 
  local currentInputDevice = hs.audiodevice.defaultInputDevice()
  local devices = hs.audiodevice.allInputDevices()

  local index = hs.fnutils.indexOf(devices, currentInputDevice)

  local device

  while true do
    device = devices[(index % #devices) + 1]
    if device == nil then
      index = index + 1
    else
      break
    end
  end

  device:setDefaultInputDevice()
  hs.alert(device:name())
end

-- 다음 키를 눌렀을 때 위의 함수를 실행
-- 이 키 매핑은 마음대로 바꿔도 됩니다.
hs.hotkey.bind({"cmd", "alt", "ctrl"}, 'o', change_output_device)
hs.hotkey.bind({"cmd", "alt", "ctrl"}, 'i', change_input_device)
```

## 설정 다시 불러오기

![](/images/hammerspoon/open-console.png)

이제 설정을 다시 불러와야 합니다. `Console...`을 누르면 다음과 같은 창이
뜨는데요.

![](/images/hammerspoon/console.png)

오른쪽 위에 있는 `Reload config`버튼을 누르면 설정을 다시 불러옵니다. 이때
출력되는 데이터에 뭔가 이상이 있는지 확인합니다. 이상이 없다면 아까 등록한
단축키를 눌러서 올바르게 되는지 확인합니다. 단축키를 누르면 다음 걸로 계속
넘어가서 단축키 한 번 만으로 입출력 장치를 변경할 수 있게 됩니다.

## 참고

- [해머스푼](https://www.hammerspoon.org/)
