# 通用API

全局表名称：ut

| API | 返回值 | 可用 | 描述 |
| :--- | :---: | :---: | :--- |
| ut.positiveMod\(int a, int b\) | int | C/S | 返回a与b求余的非负数结果。 |
| ut.randInt\(int n\) | int | C/S | 返回\[0, n\)的随机整数。 |
| ut.randIntArea\(int begin, int len\) | int | C/S | 若len大于0，返回\[begin, begin + len\)的随机整数，否则返回begin。 |
| ut.randDouble\(double value\) | double | C/S | 返回\[0, value\)的随机浮点数。 |
| ut.randDoubleArea\(double begin, double len\) | double | C/S | 若len大于0，返回\[begin, begin + len\)的随机浮点数，否则返回begin。 |
| ut.randSym\(double value\) | double | C/S | 返回\(-value, value\)的随机浮点数。 |
| ut.randTry\(int n\) | bool | C/S | 当n为正数时1/n概率返回true，否则始终返回false。 |
|  |  |  |  |



