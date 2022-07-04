# Pomodoro-Timer-App
항상 한눈파는 공부쟁이를 위한 뽀모도로 타이머 앱<br>

## 뽀모도로 타이머 앱의 기능상세
DatePicker를 통해 타이머 시간을 설정할 수 있다<br>
시작 버튼을 누르면 타이머가 시작되고 일시 정시를 누르면 타이머가 일시정지된다<br>
취소 버튼을 누르면 타이머가 종료된다<br>
카운트 다운이 완료되면 알람이 울린다<br>
<br>
## 활용 기술
DispatchSourceTimer<br>
UiView Animation<br>
<br>
## 실행 중 발생한 오류
타이머를 시작하고 일시정지하고 다시 취소버튼을 누르면 런타임 오류 발생<br>
왜???<br>
문서를 뒤져보니<br>
self.timerStatus == .pause 일 때, timer?.suspend() 메소드를 호출해서 일시정지 시키려면 stopTimer() 메소드에서 self.timer = nil을 할당하기전에, timer.resume()메소드를 호출해야 한다는 구문을 발견했다<br>
  func stopTimer(){<br>
        if self.timerStatus == .pause {<br>
            self.timer?.resume()<br>
        }<br>
        self.timerStatus = .end<br>
        self.cancelButton.isEnabled = false<br>
        self.setTimerInfoViewVisible(isHidden: true)<br>
        self.datePicker.isHidden = false<br>
        self.toggleButton.isSelected = false<br>
        self.timer?.cancel()<br>
        self.timer = nil<br>
        <br>
        <br>
    }<br>
<br>

## 완성
![스크린샷 2022-07-04 오후 4 15 38](https://user-images.githubusercontent.com/102133961/177101701-24ff2a66-fbda-488a-87e0-7597b33f1838.jpg)
![스크린샷 2022-07-04 오후 4 15 58](https://user-images.githubusercontent.com/102133961/177101769-81c5a09f-cc14-45c5-9d85-6f44b639c5f7.jpg)
![스크린샷 2022-07-04 오후 4 16 25](https://user-images.githubusercontent.com/102133961/177101825-d31d1226-fbfa-4285-9862-32952b5743cf.jpg)

