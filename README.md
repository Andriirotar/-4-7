#include <iostream>
int main() {
    const int n = 10; // Вказати розмір масиву
    double arr[n];
    std::cout << "Введіть " << n << " елемент:\n";
    for (int i = 0; i < n; ++i) {
        std::cout << "Елемент " << i + 1 << ": ";
        std::cin >> arr[i];
    }
    double maxElement = arr[0];
    int maxIndex = 0;
    for (int i = 1; i < n; ++i) {
        if (arr[i] > maxElement) {
            maxElement = arr[i];
            maxIndex = i;
        }
    }
    std::cout << "Індекс максимального елемента: " << maxIndex << std::endl;
    int firstZeroIndex = -1;
    int secondZeroIndex = -1;
    for (int i = 0; i < n; ++i) {
        if (arr[i] == 0) {
            if (firstZeroIndex == -1)
                firstZeroIndex = i;
            else {
                secondZeroIndex = i;
                break;
            }
        }
    }
    if (firstZeroIndex != -1 && secondZeroIndex != -1 && secondZeroIndex > firstZeroIndex) {
        double product = 1.0;
        for (int i = firstZeroIndex + 1; i < secondZeroIndex; ++i) {
            product *= arr[i];
        }
        std::cout << "Добуток між першим і другим нульовими елементами: " << product << std::endl;
    } else {
        std::cout << "У масиві недостатньо нульових елементів.\n";
    }
    for (int i = 0; i < n / 2; ++i) {
        if (i % 2 == 0) {
            std::swap(arr[i], arr[i + n / 2]);
        }
    }
    std::cout << "Трансформований масив:\n";
    for (int i = 0; i < n; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
    return 0;
}
