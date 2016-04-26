# 第二回活動
前回は基本的なC#の文法事項を学んだ。その中に**スコープ**があった。スコープの中で宣言した変数は、その中でだけ使用することができる。プログラミングにおいてソースコードを記述する際には、変数の使用可能な範囲を意識しよう。

~~~csharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {

    // Use this for initialization
    void Start () {
    int x;
    x = 10;
    }

    // Update is called once per frame
    void Update () {
      Debug.log("x =" + x); //Error
    }
}
~~~

### [文法]フィールド
クラススコープの中で宣言される変数のこと。

~~~csharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {
    int x; //フィールド
    // Use this for initialization
    void Start () {
    x = 10;
    }

    // Update is called once per frame
    void Update () {
      Debug.log("x = " + x); //x = 10
    }
}
~~~
---
プログラミングをする上で意識することの一つにソースコードを読みやすくするということがある。ソースコードは自分だけのものではなく、他の人と共有する資産であることを覚えておこう。

誰しも、楽をしたい。プログラミングをする上で同じものを書かないようにする。同じことを複数箇所に書いてしまうと、変更やバグが発生した場合にコードの修正が大変になる。

---
~~~csharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {
    float x; //フィールド
    // Use this for initialization
    void Start () {
    x = 10f;
    y = 20f;
    z = 5f;
    Debug.log(x + (x + y) * x - (3 * x) * 3);
    Debug.log(y + (y + z) * y - (3 * y) * 3);
    Debug.log(z + (z + x) * z - (3 * y) * 3);

    }
}
~~~
これは、単に同じ計算を値を変えて行っているだけだが、以下のようにこの計算をするという同じ動作を取り出して、まとめることだ出来る。以下のような方法を用いることがある。
~~~csharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {
    float x; //フィールド
    float y;
    float z;
    // Use this for initialization
    void Start () {
    x = 10f;
    y = 20f;
    z = 5f;
    Debug.log(mathodName(x, y));
    Debug.log(methodName(y, z));
    Debug.log(methodName(z, x));
    }

    public static float methodName(float a, float b){
      return a + (a + b) * a - (3.0 * a) * 3.0;
    }
}

~~~
まとめた場合、式を扱う部分が一箇所だけになっている。つまり、動作の内容（この場合は計算式）が変わっても変更を反映することが容易になる。

## [文法]メソッド

~~~csharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {
    float x; //フィールド
    // Use this for initialization
    void Start () {
    }

    void methodName(){ //メソッド
      //methodNameの部分には自由に名前をつけられる
      return;
    }
}
~~~
例
~~~csharp
    float plus(float a, float b){
      return a + b;
      /*returnで終わり。このブロック内でreturnの後に書いたものは実行されない。*/
    }
~~~
~~~csharp
    void OnTriggerEnter(Collider other) {
    Destroy(other.gameObject);
}
~~~
Unityの`Start()`や`Update()`もメソッドの一つだ。

**練習**
float型の変数二つを掛けてfloat値を返すメソッドmultiply()を実装しよう。

~~~csharpharp
using UnityEngine;
using System.Collections;

public class ClassName : MonoBehaviour {
    float x;
    float y;
    void Start () {
      x = 2.4;
      y = 0.3;
      Debug.log(multypliy(float a, float b)); //0.72
    }
}
~~~

---
## [文法]配列
