#include <iostream>
#include <string>
using namespace std;

class Abonent {

	int id;
	string surname, number;
	friend class Notebook;

public:

	Abonent(int Id, string Surname, string Number) {
		id = Id;
		surname = Surname;
		number = Number;
	}

	~Abonent() = default;
	
};

class Notebook {

public:
	void change(Abonent* str,int id, string numb) {
		if (str->id == id)
		{	
			str->number = numb;
			cout << "Информация обновлена" << endl;
		}
	}

	void show(Abonent* str) {
		cout << str->id << " " << str->surname << " " << str->number << " " << endl;
	}
};

int main() {
	setlocale(LC_ALL, "Russian");
	Abonent People[6] = {
		Abonent(
			0,
			"Абарникова",
			"+7 (906) 518-29-46"
		),
		Abonent(
			1,
			"Пастухова",
			"+7 (980) 234-53-30"
		),
		Abonent(
			2,
			"Клемент",
			"+7 (909) 602-28-18"
		),
		Abonent(
			3,
			"Мосенцева",
			"+7 (967) 628-71-50"
		),
		Abonent(
			4,
			"Чечина",
			"+7 (952) 820-57-29"
		),
		Abonent(
			5,
			"Корнева",
			"+7 (944) 558-89-76"
		)
	};

	int id;
	string numb;
	
	cout << "Введите id: ";
	cin >> id;
	
	cout << endl;
	cout << "Введите новый номер телефона: ";
	cin >> numb;

	Notebook notebook;

	for (auto peoples : People)
	{
		notebook.change(&peoples, id, numb);
		notebook.show(&peoples);
	}
}