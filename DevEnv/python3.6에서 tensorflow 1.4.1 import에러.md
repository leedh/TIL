# Tensorflow

## 개발환경

- OS : macOS Sierra 10.12.5
- Python : 3.6.6


tensorflow 1.4.1은 Python 3.5까지만 지원한다는 에러가 발생(현재 Python 3.6.6가 설치된 상태)

![error1](https://i.imgur.com/ZaTqnHi.png)

> RuntimeWarning: compiletime version 3.5 of module 'tensorflow.python.framework.fast_tensor_util' does not match runtime version 3.6

[JapKe님 블로그](http://im-pine.tistory.com/228)에서 1.4.0을 설치하면 된다고 하신다. (참고로 현재 기준 1.4.1이 최신버전)

필자는 macOS Sierra 10.12.5이다.
[여기](https://github.com/tensorflow/tensorflow/issues/14273)를 참고해서 다음과 같이 1.4.0 다운버전을 설치했다.
![Imgur](https://i.imgur.com/xpCpkBo.png)

> pip install --ignore-installed --upgrade "https://github.com/lakshayg/tensorflow-build/raw/master/tensorflow-1.4.0-cp36-cp36m-macosx_10_12_x86_64.whl"

tensorflow 1.4.0을 설치하니 이제 Python 3.6에서도 import된다.
![Imgur](https://i.imgur.com/yX19Xmv.png)


