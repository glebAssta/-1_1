import pytest


def isfloat(value):
    try:
        float(value)
        return True
    except ValueError:
        return False


# -----------------------------------

def test_dict_one():
    assert {"key": "value"}["key"] == "value"


def test_dict_two():
    mass = [{"a": "A", "b": "B"},
            dict([("a", "A"), ("b", "B")]),
            dict([["a", "A"], ["b", "B"]]),
            dict([["a", "A"], ("b", "B")])]
    for i in mass:
        assert dict([("a", "A"), ("b", "B")]) == i


def test_dict_three():
    assert {"a": "apple", "b": "banana"} == {"a": "banana", "b": "apple"}


def test_float_one():
    assert 1 / 2 == 0.5


def test_float_two():
    mass = ["123.456",  # десятичное число
            "      -127.2    ",  # лишние пробелы
            "\t\n12.8\r\n",  # переносы строк
            "1.797693e+308",  # Максимальное значение float
            "-5e-5"]  # отрицательная степень
    for i in mass:
        assert isfloat(i)


def test_float_three():  # из-за представления чисел в компьютере вещественные числа неточны
    assert 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 == 1  # из-за этого поялвяется данная ошибка
