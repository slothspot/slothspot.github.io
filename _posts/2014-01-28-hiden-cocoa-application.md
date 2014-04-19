---
title: Создание скрытого Cocoa приложения
layout: post
---
В процессе изучения программирования под яблочную платформу,
возникла необходимость создать приложение живущее в трее, но
не имеющее главного окна и спрятанное из дока и системного
меню.

В то время, как создание самого элемента в трее не является
проблемой (как пример, можно использовать код, приведенный
ниже:
{% highlight Objective-C %}
- (void)awakeFromNib {
  NSStatusBar *bar = [NSStatusBar systemStatusBar];
  NSStatusItem *statusItem = [bar statusItemWithLength: NSVariableStatusItemLength];
  [statusItem setTitle: @"StatusItem"];
  [statusItem setHighlightMode: YES];
}
{% endhighlight %}
), скрытие приложения из дока и системного меню оказалось не
столь очевидной задачей.

Поиск информации о том, как добиться желаемоего привел к следующему:
нам нужно фоновое приложение в терминах [Launch Services][ls]. Для
достижения этой цели нам понадобиться модифицировать Info.plist
приложения, добавив туда ключ *LSUIElement* со значением *true*:
{% highlight xml %}
  <key>LSUIElement</key>
  <true/>
{% endhighlight %}
За подробностями и дополнительной информацией обратите внимание на информацию,
приведенную по [ссылке][lsk].

[ls]: https://developer.apple.com/library/mac/documentation/Carbon/Conceptual/LaunchServicesConcepts/LSCIntro/LSCIntro.html "Launch Services Introduction"
[lsk]: https://developer.apple.com/library/mac/documentation/Carbon/Conceptual/LaunchServicesConcepts/LSCConcepts/LSCConcepts.html#//apple_ref/doc/uid/TP30000999-CH202-SW11 "Properyt List Keys for Launch Services"
