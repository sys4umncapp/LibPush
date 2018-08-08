LibPush
==========
### Functions
#### getPushData
* fun getPushData(day: Int): ArrayList<DBData>?
>저장된 Push 데이터 반환 day : 현재부터 day 만큼의 기간동안 수신한 푸시 데이터를 리턴 
>>(ex : 7 => 현재 부터 지난 7일간 푸시 수신한 데이터 반환)

#### init
* fun init(): Unit
>LibPush 초기화 시작. 앱 실행 후 한번만 호출해 주면 된다.

#### removePushData
* fun removePushData(day: Int): Unit
>저장된 Push 데이터 삭제 day : 현재부터 day 만큼의 기간동안 수신한 푸시 데이터를 삭제
>>(ex : 7 => 현재 부터 지난 7일간 푸시 수신한 데이터 삭제)

#### setBigImgSvrAddr
* fun setBigImgSvrAddr(mBigIimageServerAddress: String): LibPush?
>푸시 수신 시 Notification 영역에 표시되는 Big Image 서버 주소를 설정한다.

#### setDeviceId
* fun setDeviceId(deviceId: String): LibPush?
>디바이스를 구분하기 위한 고유 아이디를 설정한다. 설정하지 않는 경우 디폴트로 ANDROID_ID가 사용된다.

#### setLargeIcon
* fun setLargeIcon(resId: Int): LibPush?
>푸시 수신 시 Notification 영역에 표시되는 large icon 의 resource Id를 설정한다. APP icon 의 resource Id를 설정.

#### setLogEnable
* fun setLogEnable(enable: Boolean): LibPush?
>LibPush의 디버그 로그 출력 여부 설정, 디폴트는 미 출력(false) 이다.

#### setPushAgree
* fun setPushAgree(isAgree: String): LibPush?
>푸시 수신 동의 여부 설정 동의/비동의/추후설정 3가지 중 하나를 설정할 수 있다. 디폴트 값은 추후 설정이다. 설정에 사용하는 값은 Property class를 참조한다. 값이 설정되지 않은 상태에서는 설정하지 않아도 되며, 추후 사용자가 동의 여부를 결정하면 그때 호출하면 된다. 이 함수는 호출 시 즉시 서버에 반영된다. 
>>ex : LibPush.with(this).setPushAgree(Property.PUSH_AGR_Y);

#### setPushIntent
* fun setPushIntent(intent: Intent): LibPush?
>사용자가 푸시를 선택 했을 때 호출 될 Intent를 설정한다. 일반적으로 앱의 시작 Activity(MainActivity)를 파라미터로 하는 intent를 생성하여 설정. PushLib에서는 푸시 수신 시 이 intent에 push data를 intent extra로 삽입한다. 푸시 선택 시 APP은 여기서 설정한 intent를 되돌려 받게 되는데 이 intent에는 push data (title/link url 등)가 intent의 string extra 로 삽입되어 있으므로 꺼내어 사용할 수 있다. 꺼낼 때 사용하는 extra key 값들은 Property class를 참조한다.

#### setPushSvrAddr
* fun setPushSvrAddr(mPushServerAddress: String): LibPush?
>푸시 서버 주소를 설정한다.

#### setSmallIcon
* fun setSmallIcon(resId: Int): LibPush?
>푸시 수신 시 Notification 영역에 표시되는 small icon 의 resource Id를 설정한다. APP icon 의 resource Id를 설정.

### Companion Object Functions
#### with
* fun with(context: Context): LibPush?
>푸시 객체(Singleton)를 생성 한다.
<hr/>

Property
========
### Constructors
* <init>
>Property()
  
### Companion Object Properties
* INTENT_EXTRA_CONTENT>
>const val INTENT_EXTRA_CONTENT: String

* INTENT_EXTRA_IMGURL
>const val INTENT_EXTRA_IMGURL: String

* INTENT_EXTRA_LINKURL
>const val INTENT_EXTRA_LINKURL: String

* INTENT_EXTRA_TITLE
>const val INTENT_EXTRA_TITLE: String
>>수신한 푸시 데이타를 Intent에서 추출할 때 필요한 Extra 키 값

* PUSH_AGR_N
>const val PUSH_AGR_N: String

* PUSH_AGR_S
>const val PUSH_AGR_S: String

* PUSH_AGR_Y
>const val PUSH_AGR_Y: String
>>푸시 수신 동의 여부 설정 Y : 동의 N : 비동의 S : SKIP (나중에 설정 하기)
<hr/>

DBData
==========
### Constructors
* <init>
>DBData()
>>DBData(mId: Int, mTitle: String, mSubTitle: String, mBody: String, mImageUrl: String, mLinkUrl: String, mDay: String)

### Functions
* getBody
>open fun getBody(): String

* getDay
>open fun getDay(): String

* getId
>open fun getId(): Int

* getImageUrl
>open fun getImageUrl(): String

* getLinkUrl
>open fun getLinkUrl(): String

* getSubTitle
>open fun getSubTitle(): String

* getTitle
>open fun getTitle(): String

* setBody
>open fun setBody(mBody: String): Unit

* setDay
>open fun setDay(mDay: String): Unit

* setId
>open fun setId(mId: Int): Unit

* setImageUrl
>open fun setImageUrl(mImageUrl: String): Unit

* setLinkUrl
>open fun setLinkUrl(mLinkUrl: String): Unit

* setSubTitle
>open fun setSubTitle(mSubTitle: String): Unit

* setTitle
>open fun setTitle(mTitle: String): Unit

* toString
>open fun toString(): String
