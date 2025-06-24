
2025-06-22 21:39

Status:

Tags: [[notes/3 - Tags/design pattern|design pattern]] [[notes/3 - Tags/observer design pattern|observer design pattern]]
# Observer Design Pattern
Whenever there is one data change happening, a lot of people/services needs to be notified, we use observer design pattern in such cases.

Different Jargons:
	- There is a publisher who is publishing some change and there are some subscribers who have subscribed to this change. So when the change happens, all these subscribers needed to be notified.
	- There is a subject and there are observers observing the subject. Whenever there is a change in subject, all the observers needs to be notified.

Use Case:
	- You are logged into multiple devices (phone, laptop, iPad). As soon as the message comes, all these devices needs to be notified.
	- You go to Amazon and search for a product. That product is currently out of stock. You click on `Notify Me`.  Implement this `Notify Me`. (Walmart Interview Question)

##### Class Diagram

![[observer_design_pattern.png]]

```python
from abc import ABC, abstractmethod

class NotificationAlertObserver(ABC):
    @abstractmethod
    def update(self):
        pass

class StockObservable(ABC):
    @abstractmethod
    def add(self, observer):
        pass

    @abstractmethod
    def remove(self, observer):
        pass

    @abstractmethod
    def notify_subscribers(self):
        pass

    @abstractmethod
    def set_stock_count(self, new_stock_count: int):
        pass

    @abstractmethod
    def get_stock_count(self) -> int:
        pass

class Iphone(StockObservable):
    def __init__(self):
        self._observers = []
        self._stock_count = 0

    def add(self, observer):
        self._observers.append(observer)

    def remove(self, observer):
        self._observers.remove(observer)

    def notify_subscribers(self):
        for observer in self._observers:
            observer.update()

    def set_stock_count(self, new_stock_count: int):
        previous = self._stock_count
        self._stock_count = new_stock_count
        if previous == 0 and new_stock_count > 0:
            self.notify_subscribers()

    def get_stock_count(self):
        return self._stock_count

class EmailAlertObserver(NotificationAlertObserver):
    def __init__(self, email_id: str, observable: StockObservable):
        self.email_id = email_id
        self.observable = observable

    def update(self):
        self.send_mail(self.email_id, "Product is in stock, hurry up!")

    def send_mail(self, email, msg):
        print(f"Mail sent to: {email} | Message: {msg}")

class MobileAlertObserver(NotificationAlertObserver):
    def __init__(self, phone_number: str, observable: StockObservable):
        self.phone_number = phone_number
        self.observable = observable

    def update(self):
        self.send_sms(self.phone_number, "Product is in stock, hurry up!")

    def send_sms(self, phone, msg):
        print(f"SMS sent to: {phone} | Message: {msg}")

# Example usage:
if __name__ == "__main__":
    iphone = Iphone()
    email_observer = EmailAlertObserver("user@example.com", iphone)
    mobile_observer = MobileAlertObserver("1234567890", iphone)

    iphone.add(email_observer)
    iphone.add(mobile_observer)

    iphone.set_stock_count(2) # This will notify all observers
    iphone.set_stock_count(20) # This should not notify
    iphone.set_stock_count(0)
    iphone.set_stock_count(5) # This will notify all observers
```

# References
- https://sbcode.net/python/observer/#overview
- [Keerti Purswani](https://www.youtube.com/watch?v=gbTWHeGUeXs)
- [Concept and Coding](https://www.youtube.com/watch?v=Ep9_Zcgst3U)
