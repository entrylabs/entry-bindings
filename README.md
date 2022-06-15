# @entrylabs/bindings
#### forked from [@serialport/Bindings](https://serialport.io/docs/api-bindings-cpp)

## 왜 forked 되었나요?

본 라이브러리는 node-serialport 의 binding 중,  
src/serialport_win.cpp 의 `EIO_Open()` 의 `data->rtscts` 의 통신 방식이 변경된 코드입니다.
해당 통신 방식이 변경된 데에는 [엔트리](https://playentry.org/) 가 제공하는 하드웨어 중,
[햄스터](http://hamster.school/ko/) 에 관련된 하드웨어의 통신방식을 지원하기 위해서입니다.

## 사용방식

본 라이브러리는 entry-hw 및 entry-offline 에서 사용되기 위해 수정되었습니다.
해당 라이브러리에서 본 라이브러리를 설치 후 컴파일을 거쳐야 합니다.

라이브러리 설치 후,  
`electron-rebuild -v 4.0.0` 으로 설치 가능합니다. 버전은 변경될 수 있습니다.

본 라이브러리는 [@serialport/Stream](https://serialport.io/docs/api-stream) 에 종속됩니다.

함수는
```javascript
const SerialPort = require('@serialport/stream');
SerialPort.Binding = require('@entrylabs/entry-bindings');
const sp = new SerialPort();
```

혹은
```javascript
const SerialPort = require('@serialport/stream');
const binding = require('@entrylabs/entry-bindings');
const sp = new SerialPort('/dev/tty.XXX' || 'COM1', { Binding: binding });
```

과 같이 사용할 수 있습니다.
