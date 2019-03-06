
#知识点

    - 阿里强制规定代码中避免通过一个类的对象引用访问此类的静态变量或静态方法，暂时无谓增加编译器解析成本，直接用类名来访问即可
    - 利用枚举实现单例模式
	 ```
	public class ClassFactory{ 
	    private enum MyEnumSingleton{ 
	        singletonFactory; 
	        private MySingleton instance; 
	        private MyEnumSingleton(){//枚举类的构造方法在类加载是被实例化 
	            instance = new MySingleton(); 
	        } 
	        public MySingleton getInstance(){ 
	            return instance; 
	        } 
	    } 
	    public static MySingleton getInstance(){ 
	        return MyEnumSingleton.singletonFactory.getInstance(); 
	    } 
	} 
	class MySingleton{//需要获实现单例的类，比如数据库连接 Connection  
	    public MySingleton(){} 
	}
	``` 
