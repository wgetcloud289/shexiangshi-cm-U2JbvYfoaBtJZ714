
盘点5个常用的依赖注入框架，特别是前面2个。


**1、Microsoft.Extensions.DependencyInjection**


这是.Net Core框架本身内置集成的，我们只需引入Microsoft.Extensions.DependencyInjection，就可以直接使用。



```
using DependencyInjectionSample.Interfaces;
using DependencyInjectionSample.Services;

var builder = WebApplication.CreateBuilder();

builder.Services.AddRazorPages();

builder.Services.AddScoped();

var app = builder.Build();

```

**2、AutoFac**


[https://github.com/autofac/Autofac](https://github.com)


**Star：** 4\.4K


一个高级的依赖注入（DI）框架，用于.NET应用程序。它允许开发者以一种类型安全、声明式的方式编写代码，从而实现控制反转（IoC）。Autofac旨在提供强大的功能，同时保持易用性和灵活性。



```
var builder = WebApplication.CreateBuilder();

// 注册组件
builder.RegisterType<MyService>().As<IMyService>();
builder.RegisterType<AnotherService>().As<IAnotherService>().InstancePerLifetimeScope();

// 构建容器
var app= builder.Build();

// 解析服务
var myService = app.Resolve<IMyService>();

```

**3、Ninject**


[https://github.com/ninject/Ninject](https://github.com)


**Star：** 2\.7K


一个为 .NET 应用程序设计的闪电般快速、超轻量级的依赖注入器。它帮助你将应用程序分割成一系列松耦合、高内聚的组件，然后以灵活的方式将它们重新组合在一起。通过使用 Ninject 来支持你的软件架构，你的代码将变得更容易编写、重用、测试和修改。



```
public class WarriorModule : NinjectModule
{
    public override void Load() 
    {
        this.Bind().To();
    }
}

```

**4、SimpleInjector**


[https://github.com/simpleinjector/SimpleInjector](https://github.com):[CMESPEED\-楚门加速器](https://cmnspeed.com)


**Star：** 1\.2K


一个为.NET开发者设计的高效、灵活且用户友好的依赖注入库，它不仅简化了复杂的API，提供了精选的功能集，还通过其独特的装饰器注册和容器验证功能，帮助开发者遵循最佳实践，轻松构建可维护的应用程序，成为区分于其他DI容器的首选。



```
// 1. 创建容器
var container = new Container();

// 2. 配置容器（注册服务）
container.Register<IUserRepository, SqlUserRepository>(Lifestyle.Transient);
container.Register<ILogger, MailLogger>(Lifestyle.Singleton);   
container.Register<UserController>();

// 3. 验证容器配置：
container.Verify();

// 4. 注册容器为MVC的依赖解析器
DependencyResolver.SetResolver(new SimpleInjectorDependencyResolver(container));


```

**5、Windsor**


[https://github.com/castleproject/Windsor](https://github.com)


**Star：** 1\.5K


一个功能丰富、成熟稳定的控制反转（IoC）容器框架，专为 .NET 平台设计，旨在简化依赖注入并支持高度可配置的组件管理。



```
// 创建容器
var container = new WindsorContainer();

// 添加和配置组件
container.Install(FromAssembly.This());

// 解析并配置根组件及其所有依赖项
var king = container.Resolve();
king.RuleTheCastle();

// 清理容器，应用程序退出
container.Dispose();

```

\- End \-


**更多开源项目：** [https://github.com/bianchenglequ/NetCodeTop](https://github.com)


