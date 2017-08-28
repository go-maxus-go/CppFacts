1) тип результата
int / float result type? float
int * float? result type? float
1.0 type? double
1.f type? float

2) struct A { virtual void Do(int = 0){ std::cout<<"A";}};
struct B : A { virtual void Do(int){ std::cout<<"B";}};
B b;
(A&)(b).Do();
Будет вызов B.Do(0)

3) struct A { explicit A(int){} };
std::vector<A> arr;
arr.emplace_back(42);
Создаст элемент в векторе, push_back не создаст.

4) std:: string str = "hello" - литерал
    char c = 'A' - символьная константа

5) struct A { virtual Do() {std::cout << "A"; }};
struct B : A { Do() {std::cout << "B"; }};
struct C : B { Do() override {std::cout << "C"; }};
B * b = new C;
A * a = b;
a->Do(); // C
b->Do(); // C

6) std::vector<int> v1(10);
auto v2 = std::move(v1);
assert(v1.empty());
assert(v2.size() == 10);

7) std::string().c_str(); // получение C - строки (ограниченной нулем)

8) std::vector<int> v1[1000] vs std::vector<int> v2(1000)
[] - массив векторов, () - вектор с 1000 пустых элементов

9) bool, int, char - интегральные типы
интегральные + float, double - арифметические типы
class, struct, enum, enum class - пользовательские
void, void *, int &, float && - встроенные типы

10) bool преобразуется в int // false => 0, true => 1
и наоборот // false => 0, true => 1

11) auto c = L'ab'; // у меня не скомпилировалось, error C2220: warning treated as error - no 'object' file generated

12) char практически всегда 8бит, но могут быть исключения

13) 0x0123abc // шестнадцатиричный литерал
01234567 // восьмеричный литерал
123456789 // десятичный литерал
0.1f // float 0.1
0.1 // double 0.1
1.23e-1f // float
1.23e8L // long double

14) U, L - суффиксы определяют unsigned и long
1L - long 1, 2U - unsigned int 2, 3UL - unsigned long

15) все размеры типов измеряются в char, char берется за 1

16) фундаментальные типы преобразуются без потери информации, также могут преобразовываться и с потерей.

17) enum { Red, Green, Blue} // можно записывать без названия
enum State { Invalid = 1, Valid = 2, Downloaded = 4} // можно записать как флаг, State s = State(Valid | Downloaded);
enum Smth { A = -5, B = -10, C = 8} // можно задавать отрицательные значения
у енума есть диапазон, такой чтобы влезли все возможные флаги, в плюс и в минус относительно нуля.

18) extern int a; // предекларация глобальной переменной?

19) class A {}; int main() { class A; class A; } // успешно скомпилируется

20) любое объявление в котором указывается значение является определением

21) int* p, a; // *p, a
int a[10], *p[]; // a[10], *p[]
