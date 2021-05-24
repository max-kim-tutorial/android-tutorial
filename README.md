# Android Tutorial

안드로이드 살짝만 배워봅니다. 대충 어떻게 개발되는지만..


## MainActivity.java

```java
package org.techtown.hello;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

- 다른 언어의 시작점 역할을 하는 Main 함수가 없음(onCreate)
- 부모 클래스의 onCreate 함수를 호출하고 있음 
- 초기 프로젝트의 'Hello World' 텍스트는 setContentView() 함수와 이 함수에 파라미터로 전달된 R.layout.activity_main에 의해 나타난 것
- setContentView 함수는 화면에 무엇을 보여줄 것인지를 설정해주는 역할을 하고 R.layout.acitivty_main은 화면 구성 요소에 대한 정보

## res/layout/activityMain

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- 안드로이드의 마크업은 **XML**로 그린다. 스타일링도 속성으로 넘기는 모습 
- MainActivity.java에서 보았던 R.layout.activity_main과 동일
- 파일을 실행했을 때 나타나는 첫 화면의 모든 정보를 담고 있음
- 뭔가 이상한 GUI를 막 제공함(??)
- 핫리로딩 안됨?
- 이벤트 처리 : HTML과 비슷하게 속성값으로 함수 전달. 비즈니스로직이 강제로 분리(XML안에 자바 코드를 넣을수는 없어서?)
- layout 폴더 안에 레이아웃 XML을 넣어서 사용. 레이아웃들은 상하관계를 가지면서(컴포넌트처럼) 렌더링됨
- 레이아웃 만들때 대응되는 클래스가 필요함

```java
public class Fragment1 extends Fragment {
    @override
    public View onCreateView(LayoutInFlter inflater, ViewGroup container, Bundle savedInstanceState) {
        ViewGroup rootView = (ViewGroup) inflater.inflate(R.layout.fragment1, container, false);
        initUI(rootView);
        return rootView; 
    }
    private void initUi(viewGroup rootView) {
        ...
    }
}
```

```java
package org.techtown.hello;

import android.os.Bundle;
import android.view.View;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    
    // 이벤트 핸들러 함수
    public void onButton1Click(View v) {
        Toast.makeText(this, "확인 버튼이 눌렸다.", Toast.LENGTH_LONG).show();
    }
}
```

## 