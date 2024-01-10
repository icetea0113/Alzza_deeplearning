# 11장. LSTM 순환 신경망 : 도시 소음 분류 신경망
11장에서는 예제 실습을 위해 캐글의 도시소음 분류 데이터셋 파일들을 이용합니다.<br/>
도시소음 분류 데이터셋 파일들은 캐글 사이트에서 직접 다운로드 받아야 합니다.<br/>

## 캐글 사이트에서 도시소음 분류 데이터셋 다운받기
현재 캐글의 도시소음 데이터셋 페이지가 폐쇄된 상태입니다.<br/>
따라서 다음 단락의 안내에 따라 한빛미디어 홈페이지에서 데이터를 다운로드받기 바랍니다.<br/>

## 한빛 미디어 홈페이지에서 데이터셋 다운받기
깃허브 용량 관계상 도시소음 분류 데이터셋은 여기 수록하지 못하며 따라서 사용자별로 각자 다운로드받아야 합니다.<br/><br/>
한빛미디어 홈페이지의 구글드라이브 폴더의 접근 경로는 https://drive.google.com/drive/folders/1m68SdyhMZRR2q-Z5c9JNjHI-IXDGCsxs 입니다.<br/>
공개된 폴더이기 때문에 별도의 회원가입이나 로그인(Sign in) 절차는 불필요합니다.<br/>
이 폴더를 방문해 11장_urban-sound 서브폴더로 이동한 후 Train.csv 파일과 Train.tar.gz 파일을 다운로드받습니다.
이제 'tar xvzf Train.tar.gz' 명령 등을 이용해 압축을 풀면 Train 폴더 안에 다양한 도시소음 파일들이 만들어집니다.
도시소음 레이블링 정보는 Train.csv 파일 안에 있기 때문에 Train 폴더는 서브폴더 없이 모든 음원 파일을 직접 갖는 구조입니다.<br/>
실험을 위해서는 Train.csv 파일과 Train 폴더가 /data/chap11/urban-sound 폴더 밑에 위치하도록 압축 파일 해제 위치를 지정해야 합니다.<br/><br/>
한편 Train.tar.gz 파일 대신 Train.10-10.cache.gz 파일과 Train.10-100.cache.gz 파일을 다운로드받아 이용하면
다음 단락에서 설명하는 캐시 생성 단계를 생략한 채 곧바로 미리 만들어진 캐시 파일을 이용할 수 있게 됩니다.
실험의 전 과정을 볼 수 없는 대신 다운로드 시간과 실행 시간을 줄일 수 있으니 참고 바랍니다.

## 캐시 파일 생성에 대하여

반복되는 실험에서 음원 데이터의 주파수 스펙트럼 분석 부담을 줄이기 위해 예제 프로그램에서는 캐시를 생성합니다.
캐시는 외부에서 공급되지 않으며 예제 프로그램을 처음 실행시킬 때 자동생성될 것입니다.
참고로 예제 프로그램에서 만들어내는 캐시 파일의 크기는 Train.10-10.cache 파일이 819MB, Train.10-100.cache 파일이 800MB 정도입니다.
이들 캐시 파일은 데이터가 저장된 /data/chap11/urban-sound 폴더에 함께 만들어집니다.

## 11장에서 이용하는 데이터 파일
/data/chap11/urban-sound/Train.csv : 총 1 파일, 94KB<br/>
/data/chap11/urban-sound/Train/\*.wav : 총 5345 파일, 4.0GB<br/><br/>
또는<br/><br/>
/data/chap11/urban-sound/Train.csv : 총 1 파일, 94KB<br/>
/data/chap11/urban-sound/Train10-10.cache : 총 1 파일, 819MB<br/>
/data/chap11/urban-sound/Train10-100.cache : 총 1 파일, 800MB<br/><br/>