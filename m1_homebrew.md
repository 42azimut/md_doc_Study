맥북 프로 m1 을 오픈했다!
기존 맥프레는 전원이 사망했다! 배터리는 옆구리가 터져 나왔다! 사실 이상태로 거의 1년을 사용하고 있었다.
iMAC 24를 살까 했는데 어차피 확장모니터가 있어서 사용하는데는 지장은 없다! 새거가 좋긴하다!

## 홈블루 설치부터 애먹었다!
참고 사이트 https://cpuu.postype.com/post/9183991

공식 홈페이지 실리콘 설치 가이드
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

설치에는 Xcode 등 관련 추가 도구들이 설치 되는데, 완료하면 brew 경로를 등록하는 과정을 해야 한단다! <<< 이걸 몰랐다!
$ echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/cpuu/.zprofile
$ eval $(/opt/homebrew/bin/brew shellenv)

기존 인텔 맥은 /user/local 인데, 실리콘은 다른경로이므로 별도 추가 등록!

! 좋았어~ 오늘은 여기까지!!!
