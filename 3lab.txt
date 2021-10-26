#include <iostream>
#include <string>
using namespace std;

class Goods {

	int price, count;
	string name, date, number;

public:

	Goods() {
		price = 0;
		count = 0;
		name = "Null";
		date = "0-0-0000";
		number = "0";
	}

	~Goods(){
		cout << "Деструктор" << endl;
		cout << endl;
	};

	void updateGoods(string Name, string Date, int Price, int Count, string Number) {
		price = Price;
		count = Count;
		name = Name;
		date = Date;
		number = Number;
		cout << "Информация обновлена" << endl;
	}

	void show() {
		cout << "Цена: " << price << endl;
		cout << "Количество: " << count << endl;
		cout << "Наименование товара: " << name << endl;
		cout << "Дата:  " << date << endl;
		cout << "Номер накладной: " << number << endl;
		cout << "Информация выведена на экран" << endl;
	}

	int getTotalPrice() {
		return price * count;
	}

	Goods(const Goods & object) {
		price = object.price;
		count = object.count;
		name = object.name;
		date = object.date;
		number = object.number;
		cout << "Объект скопирован" << endl;
		cout << endl;
	}

};

Goods tovar(Goods &tovar) {
	cout << "Вызов функции  tovar" << endl;
	return tovar;
};

int main() {

	setlocale(LC_ALL, "Russian");
	cout << "Вход в функцию main()" << endl;
	cout << endl;

	Goods item;

	item.updateGoods("ItemName", "05-05-2021", 12, 10, "12312313123");
	cout << item.getTotalPrice() << endl;
	item.show();

	Goods itemCopy(item);
	itemCopy.show();

	cout << "Функция товар" << endl;
	tovar(item);

	cout << "Выход из функции main()" << endl;
	cout << endl;
}