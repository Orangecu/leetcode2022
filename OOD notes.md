Desigh: class level Desigh
Coding: method level

OOD vs System Design

OOD 三要素      
    1.封装 Encapsulation
        Providing onlu essential information to the 
            outside world and hiding their background details.
        Access Modifier: Public protected default private

        Visiblity ---- variable/method/class
        use Access Modifier
        control getIPAddress() <-- override 
        加密算法 公开
        密钥 私密

        开放程度：
        public      全局可见
        protected   子类可见
        package default  同package 只有同package可见
        private        只有同class 可见
        leetCode-pkg 
            leetcode1.java
                public Class code1
                    public void main{
                    }
                    private void java {
                    }

                public class code2
                
            leetcode2.java

            TreeNode.java

            class里的class （inner class）

            不可变类
                Immutabel 创建后状态不能修改 类似Final
                    input arg 不能改变
                    DB -> student class
                    thread-safe
            
            Desigh class 那个在里面定义static method（Unit method）
            class UtilsClass {
                  
            }

            

    2. 多态 Polymorphism 
        实现 Decision deferral
            Overwrite Dynamic building (run-time not compile time)
            Static method can't be overridden. b/c there is only ONE instance for static class.
        Override vs OverLoad
            重写 VS 重载
                Overload : same function name, have different # of parameters or different types of parameters RETURN_TYPE cannot be counted.

    3. 继承Inheritance
        Concept: reuse variable and method in parent class
        Inheritance and nulit inheritance: abstrace class vs interface
        Class relationship: no relationShip
        inheritance and composition
