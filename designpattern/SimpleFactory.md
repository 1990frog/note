[TOC]

定义：有一个工厂对象决定创建出哪一种产品类的实例
类型：创建型

适用场景
工厂类负责创建的对象比较少
客户端（应用层）只知道传入工厂类的参数，对于如何创建对象（逻辑）不关心

优点
只需要传入一个正确的参数，就可以获取你所需要的对象而无需知道其创建细节

缺点
工厂类的职责相对过重，增加新的产品，需要修改工厂类的判断逻辑，违背了开闭原则。无法实现基于继承的等级结构



---

反射优化简单工厂