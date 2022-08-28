# Python Basic Syntax

## 目錄
* <0> 名詞解釋
* <1> 運算子
* <2> 資料型態 & 轉換
* <3> 輸入 & 輸出
* <4> 字串
* <5> 串列
* <6> 字典
* <7> 條件判斷
* <8> 例外處理
* <9> 迴圈
* <10> 函式
* <11> 類別
---

## <0> 名詞解釋

* 基本

    ```py
    a = 1
    ```

    `a` 為 **變數 (variable)**

    `=` 為 **指派運算子 (assign operator)**

    `1` 為 **值 (value)**

    把 `1` 指派給 `a` 這個動作稱為 **賦值 (assign)**

    我們剛剛 **宣告 (declare)** 了一個變數

* 陳述式 vs 表達式

    * 表達式 (expression)

        像是 `1` , `'text'` , `0.5` , `2>1` , `False` ; 甚至 `foo()` , `myClass.myMethod()` 等有 **回傳值** 的語句都是表達式

    * 陳述式 (statement)

        除了表達式的所有語句 , 例如 **賦值** , **if-else** , **迴圈** ...等 **沒有回傳值** 的語句
---

## <1> 運算子
<http://kaiching.org/pydoing/py/python-operator.html#5>

---

## <2> 資料型態 & 轉換

### 數值型態
* 整數 (int) &rarr; `1`
    
* 浮點數 (float) &rarr; `0.5`

    * 在Python和其他大部分語言中 , `0.1 + 0.2` 不等於 `0.3` , 這是因為二進位制的關係

* 布林值 (bool) &rarr; `True` | `False`
  
    * 有 `True`(真) 和 `False`(假) 兩種

        其中 `True` 為 **除了0之外的所有數** , `False` 為 **0**

### 字串型態
* 字串 (str) &rarr; `'apple'`

    * 字串用 `'` (單引號) 或 `"` (雙引號) 包起來

    * 多行字串用 `` 或 `"""` (三引號) 包起來

        ```py
        text = '''
        這是一個多行字串
        '''
        ```

### 容器型態
* 串列 (list) &rarr; `['banana', 5]`

* 元組 (tuple) &rarr; `(1, 2)`

* 字典 (dict) &rarr; ` {'Mon':'一', 'Tue':'二'}`

* 集合 (set) &rarr; `{7, 14}`
  
### 轉換

* `float` &rarr; `int` (無條件捨去小數部分)

    ```py
    v = 1.5
    v = int(v)
    print(v)
    #output:1
    ```

* 數值 &rarr; 字串

    ```py
    a = 1
    a = str(a)
    ```

* 字串 &rarr; 數值

    ```py
    b = '0.1'
    b = float(b)

    c = '5'
    c = int(c)
    ```

* 每個型態都可以轉為 **str** , 但不是每個都轉得回來

---

## <3> 輸入 & 輸出

* `print()`

    * 括號裡放任意型態的資料

    * 用 `,` 分隔資料 , 輸出時會有一格空格分隔

        ```py
        print('Hello','World')
        #output:Hello World
        ``` 

    * `f-string` (格式化字串)
    
        在字串前加上 `f` , 字串內部的資料用 `{}` 包起來

        ```py
        a = 1
        b = 2
        print(f'{a}/{b}')
        #output:1/2
        ```

    * `sep=`
    
        分隔符號 , 預設為 **一格空白**

        ```py
        print(1,2, sep=':')
        #output:1:2
        ```

    * `end=`
    
        結尾符號 , 預設為 `\n` **換行符號**

        不想換行可以用 `end=''`

        ```py
        print('abc', end='')
        print('def', end='')
        #output:abcdef
        ```

    * `flush=True`
    
        強行重新整理 , 預設為 `False`
    
        當 print() 在迴圈裡且參數 `end` 不為預設值 `\n` 時 , 輸出就會堵塞 , 一次性輸出而非順序輸出 , 這時就需要加 `flush=True`

        ```py
        #一次性輸出的Loading bar

        import time

        print('Loading', end='')

        for i in range(6): #重複6次
            print('.', end='')
            time.sleep(0.5) #等待0.5秒
        ```

        ```py
        #正常輸出的Loading bar

        import time

        print('Loading', end='')

        for i in range(6): #重複6次
            print('.', end='', flush=True)
            time.sleep(0.5) #等待0.5秒
        ```

* `input()`

    * 括號內文字的作用為提醒使用者的文字
      
        ```py
        name = input('Enter Your Name : ')
        #output:Enter Your Name : 
        ```
    
    * 注意 : input() 回傳值皆為 `str` 型態 , 必要時需要進行轉換

        ```py
        age = int(input('Enter Your Age : '))
        ```

    * 可以用 `split()` 方法達成一行輸入多個資料

        ```py
        l = input('輸入姓名 & 年齡 (用一格空格分隔)').split(' ')
        #split()會回傳串列

        name = l[0]
        age = int(l[1])
        ```
    
## <4> 字串
* 合併字串
  
    ```py
    s = 'Hello' + 'World'
    print(s)
    #output:HelloWorld
    ```

* `f-string`

    格式化字串

    ```py
    a = 2
    b = 3

    ans = f'{a*b}'
    print(ans)
    #output:6
    ```

* 位置
  
    * 字元位置
    
        | a | p | p | l | e |
        |---|---|---|---|---|
        | 0 | 1 | 2 | 3 | 4 |
        |-5 |-4 |-3 |-2 |-1 |

    * 取字元
    
        ```py
        l = 'apple'
        l[0]  #return:a
        l[-1] #return:e
        ```

    * 取子字串
    
        ```py
        l = 'orange'
        l[0:2] #return:or
        l[3:]  #return:nge
        l[:4]  #return:oran
        ```
    
    * `find()`
    
        取得子字串位置 , 括號內放要找的字串

        ```py
        s = 'abcdef'
        s.find('a')  #return:0
        s.find('cd') #return:2  #回傳子字串首字在母字串的位置
        s.find('z')  #return:-1 #沒有找到則回傳-1
        ```
    
* `split()`
    
    分割字串
    
    `字串.split( 分隔符號(預設為一格空白) )`

    ```py
    '1 2 3'.split()
    #return:['1','2','3']

    '1.2.3'.split('.')
    #return:[1,2,3]
    ```

* `strip()`

    去除字串的首尾字串
    
    `字串.strip( 要去除的字串(預設為一格空白) )`

    ```py
    '  abc  '.strip()
    #return:abc

    '...123...'.strip('...')
    #return:123
    ```

* `replace()`

    取代字串內的字串
    
    `字串.replace( 舊字串 , 新字串 )`

    ```py
    '1 2 3'.replace(' ',',')
    #return:1,2,3
    ```

* `upper()`

    將字串轉為大寫

    `字串.upper()`

    ```py
    'Abby'.upper()
    #return:ABBY
    ```

* `lower()`

    將字串轉為小寫

    `字串.lower()`

    ```py
    'GMail'.lower()
    #return:gmail
    ```


* `len()`

    回傳字串長度(字元數量) , 也可以用在串列 & 元組 & 字典 & 集合

    `len(字串)`

    ```py
    len('Long')
    #return:4
    ```

* `str()`

    任意型態轉為字串

    `str(資料)`

    ```py
    type(str(0.5))
    #return:<class 'str'>
    ```

## <5> 串列
* 新增元素

    ```py
    l = [1, 2]
    
    #新增到尾端
    l.append(3)
    print(l)
    #output:[1, 2, 3]

    #插入到指定位置
    #insert(位置,元素)
    l.insert(0, 0.1)
    print(l)
    #output:[0.1, 1, 2, 3]
    ```

* 刪除元素

    ```py
    l = [0.1, 1, 2, 3]

    #刪除尾端元素
    l.pop()
    print(l)
    #output:[0.1, 1, 2]

    #刪除指定位置元素
    del( l[0] )
    print(l)
    #output:[1, 2]
    ```

## <6> 字典
<https://medium.com/ccclub/ccclub-python-for-beginners-tutorial-533b8d8d96f3>

---

## <7> 條件判斷
* `if`

    當...則

    ```
    if(表達式):
        # TODO
    ```

    ```py
    a = 2

    if(a>=1):
        print('Yes')

    #output:Yes
    ```

* `if-else`

    當...則... , 否則...

    ```
    if(表達式):
        # TODO
    else:
        # TODO
    ```

    ```py
    a = 0

    if(a>=1):
        print('Yes')
    else:
        print('No')
    
    #output:No
    ```

* `if-elif-else`

    當...則... , 否則如果...則... , 否則...

    注意 : 有 `elif` 就一定有 `else` , `elif` 可以有很多個

    ```
    if(表達式):
        # TODO
    elif(表達式):
        # TODO
    else:
        # TODO
    ```

    ```py
    age = 14

    if(age<14):
        print('無責任能力')
    elif(14<=age<18 or 80<=age):
        print('限制責任能力')
    else:
        print('完全責任能力')

    #output:限制責任能力
    ```

* `and` 且

    `or`  或

    ```py
    x = 14

    if(x%2==0 and x%7==0):
        print(f'{x}是2和7的公倍數')

    #output:14是2和7的公倍數
    ```

* `pass`

    不做任何事 , 可放在 `else` 語句

    ```py
    age = 14

    if(age<14):
        print('無責任能力')
    elif(14<=age<18 or 80<=age):
        print('限制責任能力')
    elif(18<=age<80):
        print('完全責任能力')
    else:
        pass
    ```

* 三元運算子

    讓 `if-else` 更簡潔

    `(TODO條件為真) if (表達式) else (TODO條件為假)`

    ```py
    score = 60

    print('PASS' if score>=60 else 'FAIL')
    
    #output:PASS
    ```

## <8> 例外處理
<https://steam.oxxostudio.tw/category/python/basic/try-except.html>

---

## <9> 迴圈
* for迴圈

    * `for 變數 in range(起始值, 終止值, 遞增(減)值):`

        * 起始值 & 終止值 & 遞增(減)值 必為 **整數**
        
            起始值 預設為 **0** , 遞增(減)值 預設為 **1**

            也可以寫成 `for i in range(次數):`

        * 起始值 $\leq$ **變數** $<$ 終止值

            變數名稱通常是 `i` , `j` , `k` . . .

        * 範例

            ```py
            for i in range(3):
                print(i)

            output:
            0
            1
            2
            ```

            ```py
            for i in range(5,2,-1):
                print(i)
            
            '''output:
            5
            4
            3'''
            ```

    * `for 變數 in 資料:`

        * 範例

            ```py
            for i in 'abc':
                print(i)

            '''output:
            a
            b
            c'''
            ```

            ```py
            for i in [0,1,2]:
                print(i)

            '''output:
            0
            1
            2'''
            ```

            ```py
            Dict = {'Mon':'一', 'Tue':'二', 'Wed':'三'}

            for i in Dict:
                print(f'{i}:{Dict[i]}')

            '''output:
            Mon:一
            Tue:二
            Wed:三'''
            ```

* while迴圈

    * `while(條件):`
      
        ```py
        i = 0

        while(i<=2):
            print(i)

        '''output:
        0
        1
        2'''
        ```

    * `while(True):`
    
        無窮迴圈
    
        按 <kbd>Ctrl</kbd> + <kbd>C</kbd> 可以中斷無窮迴圈

        ```py
        while(True):
            print('I am Infinite Loop')

        '''output:
        I am Infinite Loop
        I am Infinite Loop
        I am Infinite Loop
        I am Infinite Loop
        I am Infinite Loop
        ...
        KeyboardInterrupt'''
        ```

* `break` 中止

    ```py
    x = 5

    while(True):
    
        if(x==7):
            break
        else:
            print(x)
    
        x += 1
    
    '''output:
    5
    6'''
    ```

* `continue` 跳過本次迴圈 continue 以下內容

    ```py
    for i in range(2):
        print(f'i={i}', end='')
        print('a', end='')
        
        if(i==1):
            continue
        
        print('b', end='')

    '''output:
    i=0
    a
    b
    i=1
    a'''
    ```

## <10> 函式
* 宣告函式

    ```py
    def fun():
        print('Hello World')
    ```

* 呼叫函式

    ```py
    fun()
    #output:Hello World
    ```

* 參數

    ```py
    def plus(a,b):
        print(f'{a}+{b}={a+b}')

    plus(1,2)
    #output:1+2=3

    #也可以這樣傳入
    plus(a=3,b=4)
    #output:3+4=7
    ```

    * 預設值(當沒有傳入參數時使用預設值)

        ```py
        def welcome(user='Master'):
            print(f'Welcome, {user}.')

        welcome()
        #output:Welcome, Master.

        welcome('Mike')
        #output:Welcome, Mike.
        ```

    * 參數 vs 引數

        ```py
        def plus(x,y):
            return x+y

        a=1
        b=2
        plus(a,b)
        ```

        拿上面的例子來說

        `x` 和 `y` 是 **參數(Argument)**

        `a` 和 `b` 是 **引數(Parameter)**

* 回傳

    ```py
    def bmi(height, weight):
        return weight/(height/100)**2

    myBMI = bmi(170,50)
    print(myBMI)
    #output:17.301038062283737
    ```

    * 提示回傳值類別

        ```py
        #有回傳值

        def plus(a,b) -> int:
            return a+b

        plus(1,2)
        ```

        ```py
        #沒有回傳值

        def foo() -> None: #NoneType
            print('Welcome')

        foo()
        ```

* 全域變數 & 區域變數

    <https://ithelp.ithome.com.tw/articles/10206034>

* `global`

    在 Python 中 , 你不能在函式中直接對全域變數重新賦值(很奇怪對吧,其他語言就不會這樣) , 需要在函式裡加上 `global <variable>` 才不會出現 `UnboundLocalError` 例外

    ```py
    # Wrong

    x = 1

    def foo():
        x += 1

    foo()
    #output:UnboundLocalError
    ```

    ```py
    # Correct

    x = 1

    def foo():
        global x
        x += 1

    foo()
    print(x)
    #output:2
    ```

    要在全域使用區域變數也需要在函式裡加上 `global <variable>`

    ```py
    def foo():
        global x
        x = 50

    foo()
    x = int(x/10)
    print(x)
    #output:5
    ```

* `nonlocal`

    在函式裡的函式使用上一層的區域變數需要在本層加上 `nonlocal <variable>`

    ```py
    def fooA():
        x = 100
        def fooB():
            nonlocal x
            x = int(x/10)
            print(x)
        fooB()
    
    fooA()
    #output:10
    ```

* 觀念題

    * A.

        ```py
        x = 1

        def foo(x):
            x *= 2
            print(x)

        foo(x-8)
        #output:?
        ```

    * B.

        ```py
        x = 1

        def foo():
            global x
            x -= 5
            print(x)

        foo()
        #output:?
        ```

    * 這樣會發生什麼事 ?

        ```py
        x = 1

        def foo(x):
            global x
            x /= 10
            print(x)

        foo(x)
        #output:SyntaxError
        ```

    * 答案

        A. `14`

        B. `-4`

* 如何調用和參數名稱一樣的全域變數 ?

    ```py
    x = 1
    
    def foo(x):
        x *= 2
        globals()['x'] *= 2

        print(f'區域x: {x}')
        print(f'全域x: {globals()['x']}')

    foo(5)
    #output:
    #區域x: 10
    #全域x: 2
    ```

    `globals()` &rArr; 以字典型態回傳全域變數
    
    `locals()` &rArr; 以字典型態回傳區域變數(在全域環境下呼叫則和 `globals()` 作用相同)

## <11> 類別

類別 : <https://www.learncodewithmike.com/2020/01/python-class.html>

方法 : <https://www.learncodewithmike.com/2020/01/python-method.htm>

屬性 : <https://www.learncodewithmike.com/2020/01/python-attribute.html>

繼承 : <https://www.learncodewithmike.com/2020/01/python-inheritance.html>


---

如果你的腦袋還沒爆掉的話 , 恭喜你 , 你已經讀完了Python大部分的文法了 :)