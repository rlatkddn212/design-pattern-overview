# design-pattern-overview

디자인 패턴에 대해 정리한 문서 입니다.



## 디자인 패턴?

- GOF(Gang of Four)라는 소프트웨어 전문가 4명이 제안
- 객체지향 설계에 대한 23가지 해법 제시
- 크게 생성 패턴,  구조 패턴, 행동 패턴 3가지로 분류

  - 생성 패턴 (Creational) : 객체를 생성하는 5 가지 패턴이 있다. 직접 new로 객체를 생성하지 않고, 다른 객체를 사용하거나(팩토리), 객체를 단 하나만 생성할 수 있게 제한 하거나(싱글턴) 하여 사례에 따라 프로그램에 유연성을 향상시킬 수 있다.
  - 구조 패턴 (Structural) :  클래스에 구성을 설계하는  7 가지 패턴이 있다. 서로 다른 클래스 사이에 호환성 문제(어뎁터), 객체에 생성과 소멸 같은 기능을 대리해서 처리(프록시)등 클래스의 구성을 달리 하여 새로운 기능을 얻을 수 있다.
  - 행동 패턴 (Behavioral) : 객체 간에 커뮤니케이션 행위들에 대한 11가지 패턴이 있다. 발행자와 구독자 객체간에 커뮤니케이션(옵저버), 객체 지향 방식으로 상태 기계를 구현(상태 패턴)



## 상속보다 인터페이스

- Program to an 'interface', not an 'implementation'.
- 위 말 처럼 디자인 패턴은 인터페이스에 대한 이해가 중요
- 클래스 사용자가 클래스에 대한 구현을 모르게하고, 인터페이스를 정의하는 추상 클래스에 대해서만 알고 코드를 작성하게 한다.
- 상속보다 인터페이스를 사용하여 코드를 작성
  - 상속은 부모 클래스의 세부 사항을 알 필요가 있음
  - 부모 클래스가 변경될 경우 자식 클래스들도 수정 필요
- 부모 클래스에서 많은 구현을 하면, 자식 클래스에 자유도가 줄어든다. 부모 클래스에서 구현이 적으면, 자식 클래스들에 코드 중복이 늘어 날 수 있다.


## SOLID 원칙

- 객체지향에 5가지 원칙

- 디자인 패턴을 사용하여 SOLID 원칙에 맞게 코딩

- SOLID 원칙을 지켜 코딩 함으로써 의존성을 줄이고, 재사용성을 늘린다.

- SOLID 원칙을 지키지 않을 경우 문제점

  - 코드를 변경할 경우이다. 변경하려는 코드 부분에 의존적인 모듈을 수정해야하고, 그 모듈에 후속 변경 사항까지 연속적으로 수정해야한다. 즉, 소프트웨어를 변경하기 쉽게하려면 모듈간에 의존성을 줄여야한다.

  - 모듈에 너무 많은 기능을 추가하면, 똑같은 기능이 필요하여 만들 때도 재사용할 수 없게 만든다.



### The Single Responsibility Principle (SRP)

> 모든 클래스는 하나의 책임만 가지며, 클래스는 그 책임을 완전히 캡슐화해야 함



### The Open Closed Principle (OCP)

>  확장에는 Open, 수정에는 Close 해야한다.

- 모듈을 수정하지 않고 확장 할 수 있어야한다.



### The Liskov Substitution Principle (LSP)

> 클래스 A가 클래스 B의 부모라면 클래스 B는 클래스 A로 치환 할 수 있어야 한다.

- 정사각형과 직사각형관계로 설명하는 예가 많다.
- 정사각형을 직사각형으로 치환하여 사용할 경우 직사각형의 맴버함수로 폭을 변경시키면 정사각형의 폭과 높이가 달라진다.
- 이런 관계는 이 원칙을 위반한다고 볼 수 있다.



### The Dependency Inversion Principle (DIP)

> 추상성이 높은 클래스(interface, 부모 클래스 등)의 경우 구체클래스(구현된 클래스, 자식 클래스 등)에 의존해선 안된다.



### The Interface Segregation Principle (ISP)

> 사용자가 사용하지 않는 메서드에 의존해선 안된다.





# 생성 패턴 (Creational)




## 추상 팩토리 패턴


> 구체 클래스에 의존하지 않고 공통의 인터페이스 팩토리들을 통해 객체를 생성 


- 추상적인 공장에서 추상적인 제품을 만든다.
- 객체 지향에서 추상적인(abstract)는 구체적인 구현이 무엇인지를 생각하지 않고 인터페이스만을 생각
- 인터페이스만 사용하여 부품을 조립하고 제품을 만든다.
- 인터페이스를 구현한 하위 단계에서 구체적인 공장, 구체적인 부품, 구체적인 제품을 생산한다.

![1569141641972](https://github.com/rlatkddn212/design-pattern-overview/blob/master/image/1569141641972.png)

- 공장을 새로 추가한다면?
  - 위 다이어그램에서 공장3을 추가한다고 할때 공장 3에 제품 1, 2에 관한 메서드를 추가하는 것 이외 작업은 필요없음
- 제품을 새로 추가한다면?
  - 위 다이어그램에서 제품3을 추가한다면 공장1, 공장2에 모두 추가해줘야한다. 즉 공장이 많을 수록 복잡해진다.



### 예제

- 위키 피디아에 있는 예제를 C++로 변경한 코드 

- 각 운영체제 별로 버튼을 추가하는 예제


```c++
/**
 * 추상 팩토리 패턴
 *
 * 새로운 OS를 추가한다면?
 * 리눅스 팩토리를 추가하기만 하면됨
 *
 * 버튼이나 새로운 UI를 추가한다면?
 * 모든 운영체제에 버튼 생성을 추가해줘야함
 */
#include <iostream>
using namespace std;

struct IButton
{
	virtual ~IButton() { }
	virtual void Paint() = 0;
};

struct WinButton : IButton
{
	void Paint()
	{
		cout << "Window Button";
	}
};

struct OSXButton : IButton
{
	void Paint()
	{
		cout << "OSX Button";
	}
};

struct IGUIFactory
{
	virtual ~IGUIFactory() {}
	virtual unique_ptr<IButton> CreateButton() = 0;
};

struct WinFactory : IGUIFactory
{
	virtual unique_ptr<IButton> CreateButton()
	{
		return make_unique<WinButton>();
	}
};

struct OSXFactory : IGUIFactory
{
	virtual unique_ptr<IButton> CreateButton()
	{
		return make_unique<OSXButton>();
	}
};

int main()
{
	unique_ptr<IGUIFactory> factory;
#ifdef _WIN32
	factory = make_unique<WinFactory>();
#elif __APPLE__
	factory = make_unique<OSXFactory>();
#else

#endif	
	auto button = factory->CreateButton();
	button->Paint();

	return 0;
}
```






## 빌더 패턴

> 객체의 생성 과정과 표현 방법을 분리, 객체에 다른 표현 결과를 만들 수 있게 하는 패턴

- 복잡한 객체를 조립, 한번에 완성하기 어려운 객체
- 복잡한 객체를 단계를 밟아 만들어 나간다.

[![Builder Structure](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Builder_UML_class_diagram.svg/500px-Builder_UML_class_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Builder_UML_class_diagram.svg)

### 예제

- 카메라 앱에서 새로운 이미지를 만들어 화면에 보여준다고 해보자.
- 새로운 이미지를 만들 때 필터를 적용하고, 메이크업 해주고, 토끼 귀를 머리에 달아 줄수 있다.
- 이렇게 여러 단계를 거쳐 생성되는 작업에 빌드 패턴을 적용해 볼 수있다.
``` c++                                                                                                                                                                                                                                                                                                                                                                                                                   
/**
 * 빌더 패턴
 * 복합 객체의 생성 과정과 표현 방법을 분리하여 동일한 생성 절차에서 서로 다른 표현 결과를 만들 수 있게 하는 패턴
 * 
*/

#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
using namespace std;

struct ImageProduct
{
	ImageProduct(vector<string> v) :v(v) {}

	void Print()
	{
		for (int i = 0; i < v.size(); ++i)
		{
			cout << v[i] << endl;
		}
	}

	vector<string> v;
};

struct Builder
{
	virtual ~Builder() {}
	virtual ImageProduct Build() = 0;
	virtual Builder& WithFilter(string text) = 0;
	virtual Builder& WithMakeUp(string text) = 0;
	virtual Builder& WithStyle(string text) = 0;
};


struct ImageBuilder : public Builder
{
	~ImageBuilder() {}

	ImageProduct Build();

	Builder& WithFilter(string text)
	{
		mImageItem.push_back(make_pair("필터 : ", text));
		return *this;
	}

	Builder& WithMakeUp(string text)
	{
		mImageItem.push_back(make_pair("메이크업 : ", text));
		return *this;
	}

	Builder& WithStyle(string text)
	{
		mImageItem.push_back(make_pair("스타일 : ", text));
		return *this;
	}

	vector<pair<string, string>>	mImageItem;
};

struct Director
{
	Director(shared_ptr<Builder> builder) : builder(builder) {}
	~Director() { }
	void Construct();

private:
	shared_ptr<Builder>	builder;
};

ImageProduct ImageBuilder::Build()
{
	vector<string> v;
	for (int i = 0; i < mImageItem.size(); ++i)
	{
		v.push_back(mImageItem[i].first + mImageItem[i].second);
	}

	ImageProduct p = ImageProduct(v);
	return p;
}

void Director::Construct()
{
	builder->WithFilter("hello");
	builder->WithStyle("normal");
	builder->WithMakeUp("face");
}

int main()
{
	shared_ptr<Builder> builder(make_shared<ImageBuilder>());
	shared_ptr<Director> director(make_shared<Director>(builder));

	director->Construct();
	ImageProduct p = builder->Build();
	p.Print();

	return 0;
}
```



## 팩토리 메서드 패턴

> (공장) 객체를 사용하여 구체 객체를 생성

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/FactoryMethod.svg/300px-FactoryMethod.svg.png)

- 위 다이어그램에서 Product(구체 객체)를 생성할 때, factory객체에 도움을 받아서 생성
- 인스턴스를 생성하는 방법을 템플릿 메서드 패턴으로 한다.

``` c++
#include <iostream>
#include <string>
#include <vector>
#include <memory>
using namespace std;

class Product
{
public:
	virtual void use() = 0;
};

// 템플릿 메서드와 동일하게 부모클래스에서 대략적인 알고리즘 제공
class Factory
{
public:
	shared_ptr<Product> create(string str)
	{
		shared_ptr<Product> p = createProduct(str);
		registerProduct(p);

		return p;
	}

protected:
	virtual shared_ptr<Product> createProduct(string str) = 0;
	virtual void registerProduct(shared_ptr<Product> product) = 0;
};

class IDCard : public Product
{
public:
	IDCard(string own)
	{
		cout << "카드 생성\n";
		owner = own;
	}

	virtual void use()
	{
		cout << owner << "의 카드를 사용합니다.\n";
	}

	string GetOnwer()
	{
		return owner;
	}

private:
	string owner;
};

class IDCardFactory : public Factory
{
public:

protected:
	virtual shared_ptr<Product> createProduct(string str)
	{
		return make_shared<IDCard>(str);
	}

	virtual void registerProduct(shared_ptr<Product> product)
	{
		v.push_back(dynamic_pointer_cast<IDCard>(product)->GetOnwer());
	}

private:

	vector<string> v;
};


int main()
{
	shared_ptr<Factory> factory = make_shared<IDCardFactory>();
	shared_ptr<Product> card1 = factory->create("김상우");
	shared_ptr<Product> card2 = factory->create("ㅁㄴㅇ");
	shared_ptr<Product> card3 = factory->create("ㅂㅈㄷ");

	card1->use();
	card2->use();
	card3->use();

	return 0;
}
```


## 프로토 타입 패턴

> 객체를 처음부터 생성하지 않고, 기존에 존재하던 객체 정보들을 복제하여 새로운 객체를 생성

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Prototype_UML.svg/600px-Prototype_UML.svg.png)

- 직접 객체를 생성하지 않기 때문에 객체 생성에 대한 오버헤드가 없음
- 기존 객체가 프로토 타입 역할
- java의 경우 clone 메소드를 제공하여 객체를 복사할 수 있게 한다. C++에서는 복사 생성자를 사용하면 되겠다.


``` c++
#include <iostream>
#include <map>
#include <string>
using namespace std;

class Product
{
public:
	virtual void use(string s) = 0;
	virtual shared_ptr<Product> CreateClone() = 0;
};

class Manager
{
public:
	void Register(string name, shared_ptr<Product> proto)
	{
		m.insert(make_pair(name, proto));
	}

	shared_ptr<Product> Create(string protoName)
	{
		shared_ptr<Product> p = m[protoName];
		return p->CreateClone();
	}

private:
	map<string, shared_ptr<Product>> m;
};

class MessageBox : public Product
{
public:
	MessageBox(char ch) : messageChar(ch) {}

	void use(string s)
	{
		int length = s.size();

		for (int i = 0; i < length + 4; ++i)
		{
			cout << messageChar;
		}
		cout << "\n";
		cout << messageChar << " " << s << " " << messageChar;

		cout << "\n";

		for (int i = 0; i < length + 4; ++i)
		{
			cout << messageChar;
		}
		cout << "\n";
	}

	virtual shared_ptr<Product> CreateClone()
	{
		return make_shared<MessageBox>(*this);
	}

private:
	char messageChar;
};

int main()
{
	unique_ptr<Manager> mngr = make_unique<Manager>();
	shared_ptr<MessageBox> mb0 = make_shared<MessageBox>('*');
	shared_ptr<MessageBox> mb1 = make_shared<MessageBox>('-');

	mngr->Register("strong Message", mb0);
	mngr->Register("slash Message", mb1);

	shared_ptr<Product> p1 = mngr->Create("strong Message");
	shared_ptr<Product> p2 = mngr->Create("slash Message");
	shared_ptr<Product> p3 = mngr->Create("slash Message");

	p1->use("Hello world");
	p2->use("Hello world");
	p2->use("Hello world2");

	return 0;
}
```




## 싱글턴 패턴

> 객체를 하나만 제공한다.

- 객체를 하나만 만들 수 있다. 주로 관리 객체로 사용된다.
- 전역적으로 접근 가능하다. 그 때문에 객체지향에 원칙을 위반한다는 여론이 있다. 하지만 디자인 패턴에서 가장 많이 사용되는 패턴



### 예제

- 구현 방법이 다양한데, 기본적으로 생성자를 private으로 하고 getInstance메소드를 제공한다.
- 싱글턴 클래스를 부모로 상속 받아 사용하는 경우도 있다.

```c++
struct Manager
{
priavte:
  Manager();
public:
	Manager* getInstance()
  {
    static Manager* mngr = null;
    if (mngr == null)
    {
      mngr = new Manager();
    }
    return mngr;
  }
};
```





# 구조 패턴(Structural)




## 어댑터 패턴

> 클래스의 인터페이스를 사용자가 원하는 다른 인터페이스로 변환하는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/ClassAdapter.png/300px-ClassAdapter.png)](https://en.wikipedia.org/wiki/File:ClassAdapter.png)

- 어댑터 패턴을 이해하기 위해 주로 AC 어댑터로 설명한다.
  - 교류 220 V를 AC 어댑터를 통해 직류 5~12V로 변환 할 수 있다.
  - 클래스가 제공하는 것 (220V)을 어댑터 패턴을 통해 적절하게 연결 할 수 있다.
- 위 다이어그램에서 Adaptee가 제공해주는 것과 우리가 필요한 것을 어댑터로 연결해준다.
- wrapper 패턴이라고도 부른다.
- 주로 기존에 사용하던 클래스를 다른 곳에 재사용하고 싶은데 사용하는 인터페이스만 다르게 정의하고 싶을 때 사용된다.

``` c++
#include <iostream>
#include <string>
#include <vector>
using namespace std;

class Banner
{
public:

	Banner(string s) : str(s)
	{
	}

	void ShowWithParen()
	{
		cout << "(" << str << ")\n";
	}

	void ShowWithAster()
	{
		cout << "*" << str << "*\n";
	}

private:
	string str;
};

class Print
{
public:
	virtual ~Print() {}
	virtual void PrintWeak() = 0;
	virtual void PrintStrong() = 0;
};

class PrintBanner : public Banner, public Print
{
public:
	PrintBanner(string s) : Banner(s)
	{

	}

	void PrintWeak()
	{
		ShowWithParen();
	}

	void PrintStrong()
	{
		ShowWithAster();
	}
};

int main()
{
	string s = "Hello World!";
	Print* p = new PrintBanner(s);
	p->PrintStrong();
	p->PrintWeak();

	return 0;
}
```



## 브리지 패턴

> 기능과 구현으로 분리하여 각자 독립적으로 변형할 수 있게 하는 패턴 

[![Bridge UML class diagram.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Bridge_UML_class_diagram.svg/500px-Bridge_UML_class_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Bridge_UML_class_diagram.svg)

- 위 다이어그램에서 구현부, Abstraction이 기능(추상)부이다.
- 기능과 구현을 분리하여 구현한다.
- 기능 클래스 ? 기능을 가진 함수를 가지고 있는 클래스, 그것을 상속받아 기능을 추가된 클래스
- 구현 클래스 ? 상위 클래스는 인터페이스만 제공, 하위 클래스에서 구현을 하여 구현을 숨긴 클래스
- 기능과 구현을 둘다 가진 클래스 일 경우 이를 기능과 구현부로 분리
- 분리한 기능과 구현에 다리를 놓아 연결 시키는 패턴

``` c++
#include <iostream>
#include <string>
using namespace std;

// 구현
class DisplayImpl
{
public:
	virtual void RawOpen() = 0;
	virtual void RawPrint() = 0;
	virtual void RawClose() = 0;
private:

};

// 기능 
class Display
{
public:
	Display(shared_ptr<DisplayImpl> impl)
	{
		mImpl = impl;
	}

	void Open()
	{
		mImpl->RawOpen();
	}

	void Print()
	{
		mImpl->RawPrint();
	}

	void Close()
	{
		mImpl->RawClose();
	}

	void Show()
	{
		Open();
		Print();
		Close();
	}

private:
	shared_ptr<DisplayImpl> mImpl;
};

class CountDisplay : public Display
{
public:
	CountDisplay(shared_ptr<DisplayImpl> impl) : Display(impl) {}

	void MultiShow(int t)
	{
		Open();
		for (int i = 0; i < t; ++i)
		{
			Print();
		}

		Close();
	}

private:

};

// 구현 클래스
class StringDisplayImpl : public DisplayImpl
{
public:
	StringDisplayImpl(string s) : str(s), len(s.size())
	{
	}

	virtual void RawOpen()
	{
		printLine();
	}

	virtual void RawPrint()
	{
		cout << "|" << str << "|\n";
	}

	virtual void RawClose()
	{
		printLine();
	}

	void printLine()
	{
		cout << "+";
		for (int i = 0; i < len; ++i)
		{
			cout << "-";
		}

		cout << "+\n";
	}

private:
	string str;
	int len;
};

int main()
{
	shared_ptr<Display> d1 = make_shared<Display>(make_shared<StringDisplayImpl>("Hello, World!"));
	shared_ptr<Display> d2 = make_shared<Display>(make_shared<StringDisplayImpl>("Hello, Korea!"));

	shared_ptr<CountDisplay> d3 = make_shared<CountDisplay>(make_shared<StringDisplayImpl>("Hello, Universe!"));

	d1->Show();
	d2->Show();
	
	d3->MultiShow(5);

	return 0;
}
```

## 컴포지트 패턴

> 객체들의 관계를 트리 구조로 구성하여 부분-전체 계층을 표현하는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Composite_UML_class_diagram_%28fixed%29.svg/600px-Composite_UML_class_diagram_%28fixed%29.svg.png)](https://en.wikipedia.org/wiki/File:Composite_UML_class_diagram_(fixed).svg)

- 파일 시스템에 디렉토리 구조, 게임 엔진에 씬 트리가 대표적인 예제
- 재귀적인 구조를 만들어 내는 패턴


``` c++
#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Entry : public enable_shared_from_this<Entry>
{
public:
	virtual string GetName() = 0;
	virtual int GetSize() = 0;
	virtual shared_ptr<Entry> Add(shared_ptr<Entry> entry)
	{
		return nullptr;
	}

	virtual void PrintList()
	{
		PrintList(" ");
	}

	virtual void PrintList(string str) = 0;
	string ToString()
	{
		return GetName() + "(" + to_string(GetSize()) + ")";
	}

private:
	
};

class FileObject :public Entry
{
public:
	FileObject(string name, int size)
	{
		mName = name;
		mSize = size;
	}

	string GetName()
	{
		return mName;
	}

	int GetSize()
	{
		return mSize;
	}


protected:
	void PrintList(string str)
	{
		cout << str << "/" << mName << "(" << GetSize() << ")" << "\n";
	}

private:
	string mName;
	int mSize;
};

class Directory : public Entry
{
public:
	Directory(string name)
	{
		mName = name;
	}

	string GetName()
	{
		return mName;
	}

	int GetSize()
	{
		int size = 0;
		for (auto it : mDirectory)
		{
			size += it->GetSize();
		}

		return size;
	}

	shared_ptr<Entry> Add(shared_ptr<Entry> entry)
	{
		mDirectory.push_back(entry);

		return shared_from_this();
	}

	virtual void PrintList()
	{
		PrintList("");
	}

protected:
	void PrintList(string str)
	{
		cout << str << "/" << mName << "(" << GetSize() << ")" << "\n";

		for (auto it : mDirectory)
		{
			it->PrintList(str + "/" + mName);
		}
	}

private:
	string mName;
	vector<shared_ptr<Entry>> mDirectory;
};

int main()
{
	shared_ptr<Directory> rootDir = make_shared<Directory>("root");
	shared_ptr<Directory> binDir = make_shared<Directory>("bin");
	shared_ptr<Directory> tmpDir = make_shared<Directory>("tmp");
	shared_ptr<Directory> usrDir = make_shared<Directory>("usr");

	rootDir->Add(binDir);
	rootDir->Add(tmpDir);
	rootDir->Add(usrDir);

	binDir->Add(make_shared<FileObject>("vi", 10000));
	usrDir->Add(make_shared<FileObject>("asd", 10000));

	rootDir->PrintList();

	return 0;
}
```

## 데코레이터 패턴

> 주어진 상황 및 용도에 따라 동적으로 객체에 책임(Responsibility)을 덧붙이는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Decorator_UML_class_diagram.svg/400px-Decorator_UML_class_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Decorator_UML_class_diagram.svg)

- 양파 껍질 처럼 객체가 객체를 덮는 재귀 형태 구조를 가진다.
- 위임을 통해 기능을 확장한다.
- 데코레이터란 말 그대로 객체를 장식하는 것, 대표적으로 피자에 토핑을 올리는 예제를 생각할 수 있다.
- 덧붙일 수 있는 클래스가 많아지면 클래스 분석이 힘들어 질 수 있다.

### 예제

- 피자에 토핑을 올리고 가격을 출력하는 예제
- 피자에 치즈를 감싸고 다시 페페로니로 감싸고 있다.
- 자세히 보면 자바 IO인 stream 클래스와 흡사하다.

```c++
unique_ptr<Pizza> myPizza = make_unique<Pizza>();
myPizza = make_unique<Cheese>(move(myPizza));
myPizza = make_unique<Peperoni>(move(myPizza));

cout << myPizza->GetCost() << endl;
```

### 문자열 겹치기 예제
``` c++
#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Display
{
public:
	virtual int GetColumns() = 0;
	virtual int GetRows() = 0;

	virtual string GetRowText(int row) = 0;

	void Show()
	{
		for (int i = 0; i < GetRows(); ++i)
		{
			cout << GetRowText(i) << endl;
		}
	}
};

class StringDisplay : public Display
{
public:
	StringDisplay(string str)
	{
		mStr = str;
	}

	int GetColumns()
	{
		return mStr.size();
	}

	int GetRows()
	{
		return 1;
	}

	string GetRowText(int row)
	{
		if (row == 0)
		{
			return mStr;
		}
		else
		{
			return "";
		}
	}

private:
	string mStr;
};

class Border : public Display
{
protected:
	Border(shared_ptr<Display> disp)
	{
		mDisplay = disp;
	}

	shared_ptr<Display> mDisplay;
};

class SideBorder : public Border
{
public:
	SideBorder(shared_ptr<Display> display, char ch) : Border(display), borderChar(ch)
	{

	}

	int GetColumns()
	{
		return mDisplay->GetColumns() + 2;
	}

	int GetRows()
	{
		return mDisplay->GetRows();
	}

	string GetRowText(int row)
	{
		return borderChar + mDisplay->GetRowText(row) + borderChar;
	}

private:
	char borderChar;
};

class FullBorder : public Border
{
public:
	FullBorder(shared_ptr<Display> display) : Border(display)
	{

	}

	int GetColumns()
	{
		return mDisplay->GetColumns() + 2;
	}

	int GetRows()
	{
		return mDisplay->GetRows() + 2;
	}

	string GetRowText(int row)
	{
		if (row == 0 || row == mDisplay->GetRows() + 1)
		{
			return "+" + makeLine('-', mDisplay->GetColumns()) + "+";
		}
		else
		{
			return "|" + mDisplay->GetRowText(row - 1) + "|";
		}
	}

	string makeLine(char c, int count) 
	{
		string ret;
		ret.reserve(count);
		for (int i = 0; i < count; ++i)
		{
			ret.push_back(c);
		}

		return ret;
	}

private:
};

int main()
{
	shared_ptr<Display> b0 = make_shared<StringDisplay>("Hello, world!");
	shared_ptr<Display> b1 = make_shared<SideBorder>(b0, '+');
	shared_ptr<Display> b2 = make_shared<FullBorder>(b1);

	b0->Show();
	b1->Show();
	b2->Show();

	shared_ptr<Display> b3 = make_shared<FullBorder>(
							make_shared<SideBorder>(
							make_shared<FullBorder>(
							make_shared<StringDisplay>("Hello, world!")), '+'));

	b3->Show();
	return 0;
}
```

## 퍼사드 패턴

> 복잡한 코드에 대한 간단한 인터페이스를 제공하는 객체

[![Example of Facade design pattern in UML.png](https://upload.wikimedia.org/wikipedia/en/5/57/Example_of_Facade_design_pattern_in_UML.png)](https://en.wikipedia.org/wiki/File:Example_of_Facade_design_pattern_in_UML.png)

- 프로그램이 커져 많은 클래스들이 만들어지면 복잡해 진다.
  - 클래스간에 관계도 알아야하고, 의존성, 메소드 호출 순서 여러가지를 알 필요가 있다.
- 단순하게 접근할 수 있게 래퍼 클래스를 제공
  - Facade라는 말처럼 건물의 정면 부분(외관)만 보이도록 한다는 의미


``` c++
#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <map>
using namespace std;

struct Properties
{
	Properties()
	{
		m.insert(make_pair("a@naver.com", "a"));
		m.insert(make_pair("b@naver.com", "b"));
		m.insert(make_pair("c@daum.com", "c"));
		m.insert(make_pair("d@naver.com", "d"));
	}

	map<string, string> m;
};

class Database
{
public:
	static shared_ptr<Properties> GetProperties(string dbname)
	{
		shared_ptr<Properties> prop = make_shared<Properties>();
		return prop;
	}

private:
	Database() {}
};

class HtmlWriter
{
public:
	
	HtmlWriter(ofstream& out):fout(out)
	{
	}

	void Title(string title)
	{
		if (fout.is_open())
		{
			fout << "<html>\n";
			fout << "<head>\n";
			fout << "<title>" << title << "</title>\n";
			fout << "</head>\n";
			fout << "<body>\n";
			fout << "<h1>" << title << "</h1>\n";
		}
	}

	void Paragraph(string msg)
	{
		if (fout.is_open())
		{
			fout << "<p>"<< msg << "</p>\n";
		}
	}

	void Link(string href, string caption)
	{
		Paragraph("<a href=\"" + href + "\">" +caption + "</a>");
	}

	void MailTo(string mailaddr, string username)
	{
		Link("mailto:" + mailaddr, username);
	}
	void Close()
	{
		if (fout.is_open())
		{
			fout << "</body>\n";
			fout << "</html>\n";
		}
	}

private:
	ofstream& fout;
};

// facade 패턴
class PageMaker
{
private:
	PageMaker() {}
public:
	static void makeWelcomePage(string mailaddr, string filename)
	{
		shared_ptr<Properties> prop = Database::GetProperties(mailaddr);

		string username = prop->m[mailaddr];
		ofstream out;
		out.open(filename);
		shared_ptr<HtmlWriter> hw = make_shared<HtmlWriter>(out);
		hw->Title("Welcome to " + username + "'s page!");
		hw->Paragraph(username + "의 페이지에 오신걸 환영");
		hw->Paragraph("메일 주세요.");
		hw->MailTo(mailaddr, username);
	}
};

int main()
{
	PageMaker::makeWelcomePage("a@naver.com", "welcome.html");
	return 0;
}
```


## 플라이웨이트 패턴

>  유사한 객체들 사이에 가능한 많은 데이터를 서로 공유하도록하여 메모리 사용량을 최소화하는 패턴



- 권투에서 가장 낮은 체급이 flyweight 인데 이말 처럼 객체를 가볍게하는 패턴
- 자주 사용하는 객체를 pool에 담았다가 재사용한다.
- Pool을 클래스 형태로 구현했다고 보면될 것

``` C++
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
#include <thread>
#include <chrono>
#include <map>
#include <fstream>
using namespace std;

template<typename T>
class Singleton
{
private:
	Singleton(const Singleton&);
protected:
	Singleton() {}
public:

	static shared_ptr<T> GetInstance()
	{
		static shared_ptr<T> mngr = make_shared<T>();
		return mngr;
	}
};

class BigChar
{
public:
	BigChar(char charname)
	{
		mCharName = charname;
		mFontData = mCharName;
		switch (charname)
		{
		case '0': mFontData = "Zero";
			break;
		case '1': mFontData = "One";
			break;
		case '2': mFontData = "Two";
			break;
		case '3': mFontData = "Three";
			break;
		case '4': mFontData = "Four";
			break;
		case '5': mFontData = "Five";
			break;
		case '6': mFontData = "Six";
			break;
		case '7': mFontData = "Seven";
			break;
		case '8': mFontData = "Eight";
			break;
		case '9': mFontData = "Nine";
			break;
		default:
			mFontData = "";
		}
	}

	void Print()
	{
		cout << mFontData << endl;
	}

private:
	char mCharName;
	string mFontData;
};

class BigCharFactory : public Singleton<BigCharFactory>
{
public:
	shared_ptr<BigChar> GetBigChar(char charname)
	{
		shared_ptr<BigChar> bc = pool[charname];

		if (bc == nullptr)
		{
			bc = make_shared<BigChar>(charname);
			pool[charname] = bc;
		}

		return bc;
	}
private:
	map<char, shared_ptr<BigChar>> pool;
};

class BigString
{
public:
	BigString(string str)
	{
		mBigchars.resize(str.size());
		shared_ptr<BigCharFactory> bf = BigCharFactory::GetInstance();
		for (int i = 0; i < mBigchars.size(); ++i)
		{
			mBigchars[i] = bf->GetBigChar(str[i]);
		}
	}

	void Print()
	{
		for (int i = 0; i < mBigchars.size(); ++i)
		{
			mBigchars[i]->Print();
		}
	}

private:
	vector<shared_ptr<BigChar>> mBigchars;
};

int main()
{
	shared_ptr<BigString> bs = make_shared<BigString>("5551231");
	bs->Print();
	return 0;
}
```

## 프록시 패턴

> 대리해서 처리해주는 객체 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Proxy_pattern_diagram.svg/439px-Proxy_pattern_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Proxy_pattern_diagram.svg)


- 네트워크 처리를 해줄 때 처리시간이 적은 것과 긴것을 나눠서 처리해줄 수 있다.

``` C++
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
#include <thread>
#include <chrono>
#include <map>
#include <fstream>
using namespace std;

class Printable
{
public:
	virtual void SetPrinterName(string name) = 0;
	virtual string GetPrinterName() = 0;
	virtual void Print(string str) = 0;
};


class Printer : public Printable
{
public:
	Printer() {}
	Printer(string name)
	{
		mName = name;
		heavyJob("Print 인스턴스 생성 : " + name);
	}

	virtual void SetPrinterName(string name)
	{
		mName = name;
	}

	virtual string GetPrinterName()
	{
		return mName;
	}

	virtual void Print(string str)
	{
		cout << " == " << mName << " ==  " << endl;
		cout << str << endl;
	}

private:
	void heavyJob(string msg)
	{
		cout << msg << endl;

		for (int i = 0; i < 5; ++i)
		{
			this_thread::sleep_for(1s);
			cout << ".";
		}

		cout << "완료." << endl;
	}

	string mName;
};

class PrinterProxy : public Printable
{
public:
	PrinterProxy() {}
	PrinterProxy(string str) :mName(str) {}

	virtual void SetPrinterName(string name)
	{
		if (real != nullptr)
		{
			real->SetPrinterName(name);
		}

		mName = name;
	}

	virtual string GetPrinterName()
	{
		return mName;
	}

	virtual void Print(string str)
	{
		Realize();
		real->Print(str);
	}

	void Realize()
	{
		if (real == NULL)
		{
			real = make_shared<Printer>(mName);
		}
	}

private:
	string mName;
	shared_ptr<Printer> real;
};

int main()
{
	shared_ptr<Printable> p = make_shared<PrinterProxy>("A");
	cout << "이름 : " << p->GetPrinterName() << endl;
	p->SetPrinterName("B");
	cout << "이름 : " << p->GetPrinterName() << endl;
	p->Print("Hello World!");
	return 0;
}
```

# 행동 패턴 (Behavioral)




## 책임 연쇄 패턴

> 객체를 사슬 처럼 연결 해둔 후 연결된 사슬을 차례로 이동하면서 객체에 대한 처리를 결정한다.

[![img](https://upload.wikimedia.org/wikipedia/commons/6/6a/W3sDesign_Chain_of_Responsibility_Design_Pattern_UML.jpg)](https://en.wikipedia.org/wiki/File:W3sDesign_Chain_of_Responsibility_Design_Pattern_UML.jpg)

- 사용자가 원하는 방식으로 객체를 사슬처럼 연결한다.
- 그림에 오른쪽 시퀀스 다이어그램을 보면 시퀀스가 오른쪽으로 이동하면서 처리한다.
- 동적으로 처리를 결정할 수 있다.

``` c++
#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Trouble
{
public:
	Trouble(int num) :number(num)
	{

	}

	int GetNumber()
	{
		return number;
	}

	string GetStr()
	{
		return "[Trouble " + to_string(number) + "]";
	}

private:
	int number;
};

class Support
{
public:
	Support(string s): mName(s){}
	shared_ptr<Support> SetNext(shared_ptr<Support> next)
	{
		return mNext = next;
	}

	void DoSupport(shared_ptr<Trouble> trouble)
	{
		if (Resolve(trouble))
		{
			Done(trouble);
		}
		else if (mNext != nullptr)
		{
			mNext->DoSupport(trouble);
		}
		else
		{
			Fail(trouble);
		}
	}

protected:
	virtual bool Resolve(shared_ptr<Trouble> trouble) = 0;
	bool Done(shared_ptr<Trouble> trouble)
	{
		cout << trouble->GetStr() + " 해결됨 " + mName + "에 의해서.\n";
	}

	bool Fail(shared_ptr<Trouble> trouble)
	{
		cout << trouble->GetStr() + " 해결실패!\n";
	}

private:
	string mName;
	shared_ptr<Support> mNext;
};

class LimitSupport :public  Support
{
public:
	LimitSupport(string name, int limit) : Support(name), mLimit(limit){}

protected:
	bool Resolve(shared_ptr<Trouble> trouble)
	{
		if (trouble->GetNumber() < mLimit)
		{
			return true;
		}
		else
		{
			return false;
		}
	}

private:
	int mLimit;
};

class OddSupport :public  Support
{
public:
	OddSupport(string name) : Support(name) {}

protected:
	bool Resolve(shared_ptr<Trouble> trouble)
	{
		if (trouble->GetNumber() % 2 == 1)
		{
			return true;
		}
		else
		{
			return false;
		}
	}

private:
};


class SpecialSupport : public Support
{
public:
	SpecialSupport(string name, int number) : Support(name), mNumber(number) {}

protected:
	bool Resolve(shared_ptr<Trouble> trouble)
	{
		if (trouble->GetNumber() == mNumber)
		{
			return true;
		}
		else
		{
			return false;
		}
	}

private:
	int mNumber;
};

int main()
{
	shared_ptr<Support> a = make_shared<LimitSupport>("A", 10);
	shared_ptr<Support> b = make_shared<OddSupport>("B");
	shared_ptr<Support> c = make_shared<LimitSupport>("C", 90);
	shared_ptr<Support> d = make_shared<SpecialSupport>("D",96);
	
	a->SetNext(b)->SetNext(b)->SetNext(c)->SetNext(d);


	for (int i = 0; i < 100; ++i)
	{
		a->DoSupport(make_shared<Trouble>(i));
	}

	return 0;
}
```



## 커맨드 패턴

>요청을 객체의 형태로 캡슐화하여 사용자가 보낸 요청을 나중에 이용할 수 있도록 
>필요한 정보를 저장하고 되돌릴 수 있게 하는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/c/c8/W3sDesign_Command_Design_Pattern_UML.jpg)](https://en.wikipedia.org/wiki/File:W3sDesign_Command_Design_Pattern_UML.jpg)

- 명령을 객체로 관리한다.
- 명령집합을 저장해둔 후 이를 재사용하거나 명령을 사용하기 전으로 되돌릴 수 있다.

``` c++
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
#include <thread>
#include <chrono>
#include <map>
#include <fstream>
#include <stack>
using namespace std;

class Command
{
public:
	virtual void Execute() = 0;
};

class Drawable
{
public:
	virtual void Draw(int x, int y) = 0;
};

class MacroCommand :public Command
{
public:
	void Execute()
	{
		for (int i = 0; i < mCommands.size(); ++i)
		{
			mCommands[i]->Execute();
		}
	}

	void Append(shared_ptr<Command> command)
	{
		if (command.get() != this)
		{
			mCommands.push_back(command);
		}
	}

	void Undo()
	{
		if (!mCommands.empty())
		{
			mCommands.pop_back();
		}
	}

	void Clear()
	{
		mCommands.clear();
	}

private:
	vector<shared_ptr<Command>> mCommands;
};

class DrawCommand :public Command
{
public:
	DrawCommand(shared_ptr<Drawable> canvas, pair<int, int> p)
	{
		mDrawable = canvas;
		mPos = p;
	}

	void Execute()
	{
		mDrawable->Draw(mPos.second, mPos.first);
	}

private:
	pair<int, int> mPos;
	shared_ptr<Drawable> mDrawable;
};

class DrawCanvas : public Drawable
{
public:
	DrawCanvas(int width, int height, shared_ptr<MacroCommand> history)
		: canvas(height, vector<char>(width, ' '))
	{
		mHistory = history;
	}

	void RePaint()
	{
		for (int i = 0; i < canvas.size(); ++i)
		{
			fill(canvas[i].begin(), canvas[i].end(), ' ');
		}

		mHistory->Execute();
	}

	void Paint()
	{
		for (int i = 0; i < canvas.size(); ++i)
		{
			for (int j = 0; j < canvas[i].size(); ++j)
			{
				cout << canvas[i][j];
			}
			cout << endl;
		}
	}

	void Draw(int x, int y)
	{
		canvas[y][x] = '*';
	}

private:

	vector<vector<char>> canvas;
	shared_ptr<MacroCommand> mHistory;
};

int main()
{
	shared_ptr<MacroCommand> history = make_shared<MacroCommand>();
	shared_ptr<DrawCanvas> canvas = make_shared<DrawCanvas>(20, 10, history);

	int arr[10][2] = {
		{2,5},{1,6},{2,7},
		{2,13},{1,14},{2,15},
		{5,8},{6,9},{6,10},{5,11},
	};

	for (int i = 0; i < 20; ++i)
	{
		cout << "명령 : " << to_string(i) << endl;
		if (i < 10)
		{ 
			shared_ptr<DrawCommand> cmd = make_shared<DrawCommand>(canvas, make_pair(arr[i][0], arr[i][1]));
			history->Append(cmd);
			cmd->Execute();
			canvas->Paint();
		}
		else
		{
			history->Undo();
			canvas->RePaint();
			canvas->Paint();
		}
	}

	return 0;
}
```

## 인터프리터 패턴

> 언어에서 문법을 평가하는 방법을 클래스화한 패턴

- 정규 표현식 같은 간단한 문법 체크를 할 수 있다.
- 간단한 문법을 체크 하고 싶다면 생각해볼만 하다.
  - 수식을 읽어 그래프를 그려주는 프로그램을 만든다고 할 때 정상적인 수식인지 체크 해볼 수 있다.

``` c++
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
#include <thread>
#include <chrono>
#include <map>
#include <fstream>
#include <stack>
using namespace std;

class Context
{
public:
	Context(string str) : ss(str)
	{
		NextToken();
	}

	void SkipToken(string str)
	{
		if (str != mCurrentToken)
		{
			cout << "오류";
		}

		NextToken();
	}

	string CurrentToken()
	{
		return mCurrentToken;
	}

	int CurrentNumber()
	{
		int number = atoi(mCurrentToken.c_str());
		return number;
	}

	string NextToken()
	{
		if (getline(ss, mCurrentToken, ' '))
		{
			return mCurrentToken;
		}
		else
		{
			return mCurrentToken;
		}
	}

private:
	string mCurrentToken;
	stringstream ss;
};

class Node
{
public:
	virtual void Parse(shared_ptr<Context> context) = 0;
	virtual ostream& Print(ostream& out) = 0;

	friend ostream& operator<<(ostream& out, Node& node)
	{
		return node.Print(out);
	}
};

class CommandNode;
class RepeatCommandNode;
class PrimitiveNode;
class CommandListNode;

class ProgramNode :public Node
{
public:
	void Parse(shared_ptr<Context> context);
	virtual ostream& Print(ostream& out);
private:
	shared_ptr<CommandListNode> mCommandListNode;
};

class CommandListNode :public Node
{
public:
	void Parse(shared_ptr<Context> context);
	virtual ostream& Print(ostream& out);
private:
	vector<shared_ptr<Node>> mList;
};

class CommandNode :public Node
{
public:
	void Parse(shared_ptr<Context> context);
	virtual ostream& Print(ostream& out);

private:
	shared_ptr<Node> mNode;
};

class RepeatCommandNode :public Node
{
public:
	void Parse(shared_ptr<Context> context);
	virtual ostream& Print(ostream& out);

private:
	int mNumber;
	shared_ptr<Node> mCommandListNode;
};

class PrimitiveNode :public Node
{
public:
	void Parse(shared_ptr<Context> context);
	virtual ostream& Print(ostream& out);
private:
	string mName;
};

ostream& ProgramNode::Print(ostream& out)
{
	out << "[program " << *mCommandListNode << "]";
	return out;
}

ostream& CommandListNode::Print(ostream& out)
{
	for (int i = 0; i < mList.size(); ++i)
	{
		out << *mList[i] << " ";
	}
	return out;
}

ostream& CommandNode::Print(ostream& out)
{
	out << *mNode;
	return out;
}
ostream& RepeatCommandNode::Print(ostream& out)
{
	out << "[repeat " << to_string(mNumber) << " " << *mCommandListNode << "]";
	return out;
}
ostream& PrimitiveNode::Print(ostream& out)
{
	out << mName;
	return out;
}

void ProgramNode::Parse(shared_ptr<Context> context)
{
	context->SkipToken("program");
	mCommandListNode = make_shared<CommandListNode>();
	mCommandListNode->Parse(context);
}

void CommandListNode::Parse(shared_ptr<Context> context)
{
	while (true)
	{
		if (context->CurrentToken() == "")
		{
			cout << "파서 오류";
		}
		else if (context->CurrentToken() == "end")
		{
			context->SkipToken("end");
			break;
		}
		else
		{
			shared_ptr<Node> commandNode = make_shared<CommandNode>();
			commandNode->Parse(context);
			mList.push_back(commandNode);
		}
	}
}

void CommandNode::Parse(shared_ptr<Context> context)
{
	if (context->CurrentToken() == "repeat")
	{
		mNode = make_shared<RepeatCommandNode>();
		mNode->Parse(context);
	}
	else
	{
		mNode = make_shared<PrimitiveNode>();
		mNode->Parse(context);
	}
}

void RepeatCommandNode::Parse(shared_ptr<Context> context)
{
	context->SkipToken("repeat");
	mNumber = context->CurrentNumber();
	context->NextToken();
	mCommandListNode = make_shared<CommandListNode>();
	mCommandListNode->Parse(context);
}

void PrimitiveNode::Parse(shared_ptr<Context> context)
{
	mName = context->CurrentToken();
	context->SkipToken(mName);

	if (mName != "go" && mName != "right" && mName != "left")
	{
		cout << "파서 오류" << endl;
	}
}

int main()
{
	string arr[5]
		= {
			"program end",
			"program go end",
			"program go right go right go right go right end",
			"program repeat 4 go right end end",
			"program repeat 4 repeat 3 go right go left end right end end",
	};

	for (int i = 0; i < 5; ++i)
	{
		cout << arr[i] << endl;

		shared_ptr<Node> node = make_shared<ProgramNode>();
		node->Parse(make_shared<Context>(arr[i]));
		cout << *node << endl;
	}

	return 0;
}
```

## 반복자(Iterator) 패턴

> 반복자를 사용하여 컨테이너의 요소를 차례로 접근하는 디자인 패턴


[![img](https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Iterator_UML_class_diagram.svg/500px-Iterator_UML_class_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Iterator_UML_class_diagram.svg)


- 컨테이너를 하나씩 검색할 때 for 문을 사용하여 i를 1씩 증가시키며 찾는다.
- for문에서 사용되는 i를 추상화하는 패턴이다.
- i를 추상화하면 복잡함만 더 늘어나는게 아닐까라고 생각할 수 있겠지만, 오히려 코드가 더 유연해진다.
- 예를들어, 배열을 사용하다가 Set으로 자료구조를 변경하는 경우라면 어떨까?
- 기존에 for 반복문을 iterator를 사용한 반복문으로 변경해야 하고 여러 가지 구현들도 변경해야한다.
- 하지만 반복자 패턴을 사용하게되면, 컨테이너를 포함하고 있는 클래스만 수정해주면 되므로 다른 구현들을 건들지 않아도 된다.

``` c++

#include <iostream>
#include <string>
#include <vector>
using namespace std;

class Book
{
public:
	Book(string n) : name(n) {}
	string GetName()
	{
		return name;
	}

	string name;
};

class Iterator
{
public:
	Iterator() {}
	virtual ~Iterator() {}
	virtual bool HasNext() = 0;
	virtual Book Next() = 0;
};

class Aggregate
{
public:
	Aggregate() {}
	virtual ~Aggregate() {}
	virtual Iterator* iterator() = 0;
};


class BookShelf :public Aggregate
{
public:
	BookShelf() {}
	Book GetBookAt(int idx) 
	{
		return books[idx];
	}

	void AppendBook(Book book)
	{
		books.push_back(book);
	}

	int GetLength() 
	{
		return books.size();
	}

	Iterator* iterator();

private:
	vector<Book> books;
};

class BookShelfIterator : public Iterator
{
public:
	BookShelfIterator(BookShelf* bookShelf)
	{
		mBookShelf = bookShelf;
		idx = 0;
	}

	bool HasNext()
	{
		if (idx < mBookShelf->GetLength())
		{
			return true;
		}

		return false;
	}

	Book Next()
	{
		Book book = mBookShelf->GetBookAt(idx);
		idx++;
		return book;
	}

private:
	BookShelf* mBookShelf;
	int idx;
};

Iterator* BookShelf::iterator()
{
	return new BookShelfIterator(this);
}

int main()
{
	BookShelf bookShelf;
	Book book1("Hello world");
	Book book2("C++");
	bookShelf.AppendBook(book1);
	bookShelf.AppendBook(book2);

	BookShelfIterator iter(&bookShelf);

	while (iter.HasNext())
	{
		Book book = iter.Next();
		cout << book.GetName() << endl;
	}
}

```

## 중재자 패턴

> 모든 클래스간의 복잡한 로직을 캡슐화하고, 하나의 클래스에 위임하여 처리

[![img](https://upload.wikimedia.org/wikipedia/commons/9/92/W3sDesign_Mediator_Design_Pattern_UML.jpg)](https://commons.wikimedia.org/wiki/File:W3sDesign_Mediator_Design_Pattern_UML.jpg)

- 여러 클래스가 서로를 호출하는 것보다 중계인을 통해 접근하여 처리되도록한다.
- 클래스가 서로 A->B, B->C, C->D, D->A 이런식으로 호출 관계가 복잡할 경우
- A->M, B->M, C->M, D->M, M->A, M->B, M->C, M->D 이런식으로 호출관계를 클래스 M이 관리하도록 한다.

### 예제 : 대략적인 구조

``` c++
#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <map>
using namespace std;

class Mediator : public enable_shared_from_this<Mediator>
{
public:
	virtual void CreateColleagues() = 0;
	virtual void ColleagueChanged() = 0;
};

class Colleague
{
public:
	virtual void SetMediator(shared_ptr<Mediator> mediator) = 0;
	virtual void SetColleagueEnabled(bool isEnabled) = 0;
};

class ColleagueButton : public Colleague
{
public:
	ColleagueButton()
	{

	}

	virtual void SetMediator(shared_ptr<Mediator> mediator)
	{
		mMediator = mediator;
	}

	virtual void SetColleagueEnabled(bool isEnabled)
	{

	}

private:
	shared_ptr<Mediator> mMediator;
};

class ColleagueTextField : public Colleague
{
public:
	ColleagueTextField()
	{

	}

	virtual void SetMediator(shared_ptr<Mediator> mediator)
	{
		mMediator = mediator;
	}

	virtual void SetColleagueEnabled(bool isEnabled)
	{

	}

private:
	shared_ptr<Mediator> mMediator;
};

class ColleagueCheckBox : public Colleague
{
public:
	ColleagueCheckBox()
	{

	}

	virtual void SetMediator(shared_ptr<Mediator> mediator)
	{
		mMediator = mediator;
	}

	virtual void SetColleagueEnabled(bool isEnabled)
	{

	}

private:
	shared_ptr<Mediator> mMediator;
};

class LoginFrame : public Mediator
{
public:
	LoginFrame() : Mediator()
	{
		CreateColleagues();
	}

	void CreateColleagues()
	{
		mButton0 = make_shared<ColleagueButton>();
		mButton1 = make_shared<ColleagueButton>();
		mCheckBox0 = make_shared<ColleagueCheckBox>();
		mCheckBox1 = make_shared<ColleagueCheckBox>();
		mTextField0 = make_shared<ColleagueTextField>();
		mTextField1 = make_shared<ColleagueTextField>();

		mButton0->SetMediator(shared_from_this());
		mButton1->SetMediator(shared_from_this());
		mCheckBox0->SetMediator(shared_from_this());
		mCheckBox1->SetMediator(shared_from_this());
		mTextField0->SetMediator(shared_from_this());
		mTextField1->SetMediator(shared_from_this());
	}


	virtual void ColleagueChanged()
	{

	}

private:
	shared_ptr<ColleagueButton> mButton0;
	shared_ptr<ColleagueButton> mButton1;

	shared_ptr<ColleagueCheckBox> mCheckBox0;
	shared_ptr<ColleagueCheckBox> mCheckBox1;

	shared_ptr<ColleagueTextField> mTextField0;
	shared_ptr<ColleagueTextField> mTextField1;
};

int main()
{
	return 0;
}
```


## 메멘토 패턴

> 객체를 이전 상태로 되돌릴 수 있는 기능을 제공하는 소프트웨어 디자인 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/3/38/W3sDesign_Memento_Design_Pattern_UML.jpg)](https://en.wikipedia.org/wiki/File:W3sDesign_Memento_Design_Pattern_UML.jpg)

- 커맨드 패턴과 동일하게 이전 상태로 되돌릴수 있는 기능을 제공한다.
  - 커맨드 패턴은 커맨드 객체가 명령을 저장해 둔 후 직접 다른 객체에 그 명령 실행 시킨다.
  - 매멘토 패턴은 메멘토 객체가 다른 객체에 포함되어 상태 기록을 도와준다.
  - 커맨드 객체가 메멘토 패턴으로 구현되어 undo나 redo를 사용할 수도 있다.

``` c++
#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <map>
using namespace std;

class Memento
{
public:
	Memento(int money)
	{
		mMoney = money;
	}
	
	int GetMoney()
	{
		return mMoney;
	}

	void AddFruit(string fruit)
	{
		mFruits.push_back(fruit);
	}
	vector<string> GetFruits()
	{
		return mFruits;
	}
private:
	int mMoney;
	vector<string> mFruits;
};

class Gamer
{
public:
	Gamer(int money)
	{
		mMoney = money;
	}

	void Bet()
	{
		int dice = rand() % 6 + 1;

		if (dice == 1)
		{
			cout << "100원 증가" << endl;
			mMoney += 100;
		}
		else if (dice == 2)
		{
			cout << "절반 날아감" << endl;
			mMoney /= 2;
		}
		else if (dice == 6)
		{
			string f = GetFruit();
			cout << f << "를 받았습니다." << endl;
			mFruits.push_back(f);
		}
		else
		{
			cout << "변한것 없음" << endl;
		}
	}

	shared_ptr<Memento> CreateMemento()
	{
		shared_ptr<Memento> m = make_shared<Memento>(mMoney);

		for (int i = 0; i < mFruits.size(); ++i)
		{
			if (strncmp(mFruits[i].c_str(), "맛나는 ", 8))
			{
				m->AddFruit(mFruits[i]);
			}
		}

		return m;
	}

	void RestoreMemento(shared_ptr<Memento> memento)
	{
		mMoney = memento->GetMoney();
		mFruits = memento->GetFruits();
	}

	string GetFruit()
	{
		string prefix = "";
		if (rand() % 2 == 0)
		{
			prefix += "맛나는 ";
		}
		return  prefix + Fruits_Name[rand() % 4];
	}

	int GetMoney()
	{
		return mMoney;
	}
	
	void PrintFruits()
	{
		for (int i = 0; i < mFruits.size(); ++i)
		{
			cout << mFruits[i];
		}
	}

	friend ostream& operator<<(ostream& out, const Gamer& gamer);

private:
	int mMoney;
	vector<string> mFruits;
	
	string Fruits_Name[4] = { "사과", "포도", "바나나", "귤" };
};

ostream& operator<<(ostream& out, Gamer& gamer)
{
	out << "[money = " << to_string(gamer.GetMoney()) + ", fruits = ";
	gamer.PrintFruits();
	out << "]\n";

	return out;
}

int main()
{
	shared_ptr<Gamer> gamer = make_shared<Gamer>(100);
	shared_ptr<Memento> memento = gamer->CreateMemento();

	for (int i = 0; i < 100; ++i)
	{
		cout << "=============== " + to_string(i) << endl;
		cout << "현상 : " << *gamer;

		gamer->Bet();

		cout << "소지금 : " + to_string(gamer->GetMoney()) + " 원이 되었습니다.\n";

		if (gamer->GetMoney() > memento->GetMoney())
		{
			cout << "상태 저장" << endl;
			memento = gamer->CreateMemento();
		}
		else if (gamer->GetMoney() < memento->GetMoney())
		{
			cout << "상태 복원" << endl;
			gamer->RestoreMemento(memento);
		}
	}

	return 0;
}
```


## 옵저버 패턴

> 관찰 대상이 되는 객체에 상태가 변경될 경우 옵저버 객체들에게 통보해주는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/0/01/W3sDesign_Observer_Design_Pattern_UML.jpg)](https://en.wikipedia.org/wiki/File:W3sDesign_Observer_Design_Pattern_UML.jpg)

- subject객체를 옵저버들이 관찰하고 있는게 아니라 subject 객체가 변경될 경우 옵저버들에게 통보(notify) 해주는 방식
  - 옵저버는 구독만 해두고 아무 행동도 취하지 않음.. 전혀 관찰하고 있지 않다.
  - 때문에 publish-subscribe 패턴이라고도 불린다.

``` c++
#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <map>
using namespace std;

class NumberGenerator;
class Observer
{
public:
	virtual void Update(shared_ptr<NumberGenerator> generator) = 0;
};

class NumberGenerator : public enable_shared_from_this<NumberGenerator>
{
public:
	void AddObserver(shared_ptr<Observer> observer)
	{
		mObservers.push_back(observer);
	}

	void DeleteObserver(shared_ptr<Observer> observer)
	{

	}

	void NotifyObserves()
	{
		for (int i = 0; i < mObservers.size(); ++i)
		{
			mObservers[i]->Update(shared_from_this());
		}
	}

	virtual int GetNumber() = 0;
	virtual void Execute() = 0;

private:
	vector<shared_ptr<Observer>> mObservers;
};

class RandomeNumberGenerator : public NumberGenerator
{
public:
	int GetNumber()
	{
		return mNumber;
	}

	void Execute()
	{
		for (int i = 0; i < 100; ++i)
		{
			mNumber = rand() % 100;
			NotifyObserves();
		}
	}

private:
	int mNumber;
};

class DigitObserver :public Observer
{
public:
	void Update(shared_ptr<NumberGenerator> generator)
	{
		cout << "DigitObserver : " + to_string(generator->GetNumber()) << endl;
	}
};

class GraphObserver :public Observer
{
public:
	void Update(shared_ptr<NumberGenerator> generator)
	{
		cout << "GraphObserver" << endl;
		int count = generator->GetNumber();

		for (int i = 0; i < count; ++i)
		{
			cout << "*";
		}
		cout << endl;

	}
};

int main()
{
	shared_ptr<NumberGenerator> generate = make_shared<RandomeNumberGenerator>();

	shared_ptr<Observer> observer0 = make_shared<DigitObserver>();
	shared_ptr<Observer> observer1 = make_shared<GraphObserver>();

	generate->AddObserver(observer0);
	generate->AddObserver(observer1);

	generate->Execute();
	return 0;
}
```



## 상태 패턴

> 객체 지향 방식으로 상태 기계를 구현하는 디자인 패턴

![img](https://upload.wikimedia.org/wikipedia/commons/e/ec/W3sDesign_State_Design_Pattern_UML.jpg)

- 상태를 클래스로 표현한다.
- 객체 내부에서 상태 변경이 가능하다.

``` c++
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <memory>
#include <thread>
#include <chrono>
#include <fstream>
using namespace std;

template<typename T>
class Singleton
{
private:
	Singleton(const Singleton&);
protected:
	Singleton() {}
public:

	static shared_ptr<T> GetInstance()
	{
		static shared_ptr<T> mngr = make_shared<T>();
		return mngr;
	}
};

class State;
class NightState;
class DayState;

class Context : public enable_shared_from_this<Context>
{
public:
	virtual void ChangeState(shared_ptr<State> state) = 0;
	virtual void CallSecurityCenter(string str) = 0;
	virtual void RecordLog(string str) = 0;
	virtual void SetClock(int time) = 0;
};

class State
{
public:
	virtual void DoClock(shared_ptr<Context> context, int hour) = 0;
	virtual void DoUse(shared_ptr<Context> context) = 0;
	virtual void DoAlarm(shared_ptr<Context> context) = 0;
	virtual void DoPhone(shared_ptr<Context> context) = 0;
};

class DayState : public Singleton<DayState>, public State
{
public:

	virtual void DoClock(shared_ptr<Context> context, int hour);

	virtual void DoUse(shared_ptr<Context> context)
	{
		context->RecordLog("금고 사용 (주간)");
	}

	virtual void DoAlarm(shared_ptr<Context> context)
	{
		context->CallSecurityCenter("비상벨 (주간)");
	}
	
	virtual void DoPhone(shared_ptr<Context> context)
	{
		context->CallSecurityCenter("일반 통화 (주간)");
	}

};

class NightState : public Singleton<NightState>, public State
{
public:

	virtual void DoClock(shared_ptr<Context> context, int hour);

	virtual void DoUse(shared_ptr<Context> context)
	{
		context->CallSecurityCenter("야간 금고 사용 (야간)");
	}

	virtual void DoAlarm(shared_ptr<Context> context)
	{
		context->CallSecurityCenter("삐요삐요(야간)");
	}

	virtual void DoPhone(shared_ptr<Context> context)
	{
		context->CallSecurityCenter("따르릉(야간)");
	}

};

void DayState::DoClock(shared_ptr<Context> context, int hour)
{
	if (hour < 9 || 17 <= hour)
	{
		cout << "상태 변경 : 야간" << endl;
		context->ChangeState(NightState::GetInstance());
	}
}

void NightState::DoClock(shared_ptr<Context> context, int hour)
{
	if (9 <= hour && hour < 17)
	{
		cout << "상태 변경 : 주간" << endl;
		context->ChangeState(DayState::GetInstance());
	}
}

class SafeSystem :public Context
{
public:
	SafeSystem()
	{
		mState = DayState::GetInstance();
	}

	virtual void ChangeState(shared_ptr<State> state)
	{
		mState = state;
	}

	virtual void CallSecurityCenter(string str)
	{
		cout << "[경보] : " << str << endl;
	}

	virtual void RecordLog(string str)
	{
		cout << "[기록] : " << str << endl;
	}

	virtual void SetClock(int time)
	{
		cout << "현재 시간 : "  << time << ":00" << endl;
		mState->DoClock(shared_from_this(), time);
	}

	// 랜덤으로 액션 발생
	virtual void Action()
	{
		int random = rand() % 10;

		if (random == 0)
		{
			cout << "@@비상벨 사용@@" << endl;
			mState->DoAlarm(shared_from_this());
		}
		else if (random == 2)
		{
			cout << "@@금고 사용@@" << endl;
			mState->DoUse(shared_from_this());
		}
		else if (random ==3)
		{
			cout << "@@통화 사용@@" << endl;
			mState->DoPhone(shared_from_this());
		}
		else
		{
			// 아무것도 안함
		}

	}

private:
	shared_ptr<State> mState;
};

int main()
{
	shared_ptr<SafeSystem> system = make_shared<SafeSystem>();
	while (true)
	{
		for (int i = 0; i < 24; ++i)
		{
			system->SetClock(i);
			system->Action();
			this_thread::sleep_for(1s);
		}
	}

	return 0;
}
```


## 전략 패턴

> 실행 중에 알고리즘을 선택할 수 있게 하는 디자인 패턴

![img](https://upload.wikimedia.org/wikipedia/commons/4/45/W3sDesign_Strategy_Design_Pattern_UML.jpg)

- 상태 패턴과 클래스 다이어그램이 동일하다. 시퀀스 다이어그램에 처리 방식이 다른 것을 확인할 수 있다.
  - 전략 패턴은 전략 객체 내부에서 상태를 변경하지 않고 외부에서 변경하여 적절한 알고리즘을 선택한다.
- 알고리즘(전략)을 교체하여 같은 문제를 다른 방법으로 해결한다.

``` c++
#include <iostream>
#include <vector>
using namespace std;

enum MUK_CHI_BA
{
	MUK,
	CHI,
	BA,
};

class Hand
{
public:
	Hand(MUK_CHI_BA mcb)
	{
		mHandValue = mcb;
	}

	bool IsStrongerThan(shared_ptr<Hand> h)
	{
		return Fight(h) == 1;
	}

	int Fight(shared_ptr<Hand> h)
	{
		if (this == h.get())
		{
			return 0;
		}
		else if ((this->mHandValue + 1) % 3 == h->mHandValue)
		{
			return 1;
		}
		else
		{
			return -1;
		}
	}

	static shared_ptr<Hand> GetHand(int k)
	{
		return h[k];
	}

private:
	static vector<shared_ptr<Hand>> h;

	MUK_CHI_BA mHandValue;
};

vector<shared_ptr<Hand>> Hand::h =
{
	make_shared<Hand>(MUK),
	make_shared<Hand>(CHI),
	make_shared<Hand>(BA),
};

class Strategy
{
public:
	virtual shared_ptr<Hand> NextHand() = 0;
	virtual void study(bool bWin) = 0;

private:

};

class AStrategy : public Strategy
{
public:
	virtual shared_ptr<Hand> NextHand()
	{
		if (!mbWin)
		{
			prevHand = Hand::GetHand(0);
		}

		return prevHand;
	}

	virtual void study(bool bWin)
	{
		mbWin = bWin;
	}

private:
	bool mbWin;
	shared_ptr<Hand> prevHand;
};

class BStrategy : public Strategy
{
	virtual shared_ptr<Hand> NextHand()
	{
		return Hand::GetHand(rand() % 3);
	}

	virtual void study(bool bWin)
	{
		mbWin = bWin;
	}

private:
	bool mbWin;
	shared_ptr<Hand> prevHand;

};

class CStrategy : public Strategy
{
	virtual shared_ptr<Hand> NextHand()
	{
		if (!mbWin)
		{
			prevHand = Hand::GetHand(rand() % 3);
		}

		return prevHand;
	}

	virtual void study(bool bWin)
	{
		mbWin = bWin;
	}

private:
	bool mbWin;
	shared_ptr<Hand> prevHand;

};

class Player
{
public:
	Player(shared_ptr<Strategy> strategy)
	{
		mStrategy = strategy;
	}

	shared_ptr<Hand> NextHand()
	{
		return mStrategy->NextHand();
	}

	void win()
	{
		mStrategy->study(true);
	}
	void lose()
	{
		mStrategy->study(false);
	}
	void even()
	{

	}

private:
	shared_ptr<Strategy> mStrategy;
	int prevHandValue = 0;
	int currentHandValue = 0;
};


int main()
{
	shared_ptr<Player> player0 = make_shared<Player>(make_shared<AStrategy>());
	shared_ptr<Player> player1 = make_shared<Player>(make_shared<BStrategy>());

	for (int i = 0; i < 100; ++i)
	{
		shared_ptr<Hand> h0 = player0->NextHand();
		shared_ptr<Hand> h1 = player1->NextHand();

		if (h0->IsStrongerThan(h1))
		{
			cout << "p0 승리\n";
			player0->win();
			player1->lose();
		}
		else if (h1->IsStrongerThan(h0))
		{
			cout << "p1 승리\n";
			player0->win();
			player1->lose();
		}
		else
		{
			cout << "무승부 .. \n";
			player0->even();
			player1->even();
		}
	}

	return 0;
}
```

## 템플릿 메소드 패턴

> 알고리즘 뼈대를 정의하는 패턴

[![img](https://upload.wikimedia.org/wikipedia/commons/2/2a/W3sDesign_Template_Method_Design_Pattern_UML.jpg)](https://en.wikipedia.org/wiki/File:W3sDesign_Template_Method_Design_Pattern_UML.jpg)


- 상위 클래스에서 알고리즘이 추상적으로 정의되어 있고, 하위 클래스에서 이를 구현한다.
- 사용자가 클래스를 상속 받아 하위 클래스에서 primitive1,primitive2를 구현할 수 있다.
- 상위 클래스와 하위 클래스가 강하게 연결되어 연락을 주고 받는다.
- 상위 클래스의 내용을 모르면 하위 클래스를 구현하기 힘들다.

``` c++
#include <iostream>
#include <string>
using namespace std;


class AbstractDisplay
{
public:
	virtual void Open() = 0;
	virtual void Print() = 0;
	virtual void Close() = 0;
	
	// Open Print Close를 하위 클래스에서 구현하면 Display가 동작
	void Display()
	{
		Open();
		for (int i = 0; i < 10; ++i)
		{
			Print();
		}

		Close();
	}
};

class CharDisplay : public AbstractDisplay
{
public:
	CharDisplay(char c)
	{
		chr = c;
	}

	virtual void Open()
	{
		cout << "<<";
	}

	virtual void Print()
	{
		cout << chr;
	}

	virtual void Close()
	{
		cout << ">>\n";
	}

private:
	char chr;
};

class StringDisplay : public AbstractDisplay
{
public:
	StringDisplay(string s)
	{
		str = s;
	}

	virtual void Open()
	{
		cout << "+";
		for (int i = 0; i < str.size(); ++i)
			cout << "-";
		cout << "+\n";
	}

	virtual void Print()
	{
		
			cout << "|";
			cout << str;
			cout << "|\n";
	}

	virtual void Close()
	{
		cout << "+";
		for (int i = 0; i < str.size(); ++i)
			cout << "-";
		cout << "+";
	}

private:
	string str;
};


int main()
{
	AbstractDisplay* cd = new CharDisplay('H');
	AbstractDisplay* sd = new StringDisplay("Hello World");

	cd->Display();
	sd->Display();

	delete cd;
	delete sd;

	return 0;
}

```


## 비지터 패턴

> 기존 클래스 계층 구조에 변경없이 처리(behavior)를 추가하는 패턴

[![img](https://upload.wikimedia.org/wikipedia/en/thumb/e/eb/Visitor_design_pattern.svg/430px-Visitor_design_pattern.svg.png)](https://en.wikipedia.org/wiki/File:Visitor_design_pattern.svg)

- 이미 만들어진 클래스가 있을 때, 새로운 기능을 추가하고 싶다면 비지터 패턴을 고려해볼 수 있다.
- 기존 클래스의 구조를 수정하지 않고 확장하기 때문에 Open-closed prineiple을 만족한다.
- 추가 기능이 필요할 경우 Visitor를 상속 받아 구체 Visitor를 만들어 적용시켜 주면된다.


``` C++
#include <iostream>
#include <vector>
#include <string>
using namespace std;
class Element;
class File;
class Directory;
class Visitor : public enable_shared_from_this<Visitor>
{
public:
	virtual void Visit(shared_ptr<Element> file) = 0;
};

class ListVisitor :public Visitor
{
public:
	virtual void Visit(shared_ptr<Element> file);

private:
	string currentdir;
};

class Element {
public:
	virtual void accept(shared_ptr<Visitor> v) = 0;
};

class Entry : public Element, public enable_shared_from_this<Entry>
{
public:
	virtual string GetName() = 0;
	virtual int GetSize() = 0;
	virtual shared_ptr<Entry> Add(shared_ptr<Entry> entry)
	{
		return nullptr;
	}

	virtual void PrintList()
	{
		PrintList(" ");
	}

	virtual void PrintList(string str) = 0;
	string ToString()
	{
		return GetName() + "(" + to_string(GetSize()) + ")";
	}

private:

};

class File :public Entry
{
public:
	File(string name, int size)
	{
		mName = name;
		mSize = size;
	}

	string GetName()
	{
		return mName;
	}

	int GetSize()
	{
		return mSize;
	}

	virtual void accept(shared_ptr<Visitor> v)
	{
		v->Visit(shared_from_this());
	}

protected:
	void PrintList(string str)
	{
		cout << str << "/" << mName << "(" << GetSize() << ")" << "\n";
	}

private:
	string mName;
	int mSize;
};

class Directory : public Entry
{
public:
	Directory(string name)
	{
		mName = name;
	}

	string GetName()
	{
		return mName;
	}

	int GetSize()
	{
		int size = 0;
		for (auto it : mDirectory)
		{
			size += it->GetSize();
		}

		return size;
	}

	shared_ptr<Entry> Add(shared_ptr<Entry> entry)
	{
		mDirectory.push_back(entry);

		return shared_from_this();
	}

	virtual void PrintList()
	{
		PrintList("");
	}

	vector<shared_ptr<Entry>> GetDir()
	{
		return mDirectory;
	}

	virtual void accept(shared_ptr<Visitor> v)
	{
		v->Visit(shared_from_this());
	}

protected:
	void PrintList(string str)
	{
		cout << str << "/" << mName << "(" << GetSize() << ")" << "\n";

		for (auto it : mDirectory)
		{
			it->PrintList(str + "/" + mName);
		}
	}

private:
	string mName;
	vector<shared_ptr<Entry>> mDirectory;
};

void ListVisitor::Visit(shared_ptr<Element> element)
{
	shared_ptr<File> file = dynamic_pointer_cast<File>(element);
	if (file)
	{
		cout << currentdir << "/" << file->GetName() << "\n";
	}
	
	shared_ptr<Directory> dir = dynamic_pointer_cast<Directory>(element);
	if (dir)
	{
		cout << currentdir << "/" << dir->GetName() << "\n";
		string saveDir = currentdir;
		currentdir = currentdir + "/" + dir->GetName();

		for (auto it : dir->GetDir())
		{
			it->accept(shared_from_this());
		}
	}
}

int main()
{
	shared_ptr<Directory> rootDir = make_shared<Directory>("root");
	shared_ptr<Directory> binDir = make_shared<Directory>("bin");
	shared_ptr<Directory> tmpDir = make_shared<Directory>("tmp");
	shared_ptr<Directory> usrDir = make_shared<Directory>("usr");

	rootDir->Add(binDir);
	rootDir->Add(tmpDir);
	rootDir->Add(usrDir);

	binDir->Add(make_shared<File>("vi", 10000));
	usrDir->Add(make_shared<File>("asd", 10000));

	rootDir->accept(make_shared<ListVisitor>());

	return 0;
}
```


## 참고 자료 

https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf

Java 언어로 배우는 디자인 패턴 입문

위키피디아
