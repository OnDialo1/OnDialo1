#include <iostream>
#include <limits>
#include <cmath>
#include <cstring>

using namespace std;

// Función para calcular el factorial de un número
int calcularFactorial(int num) {
    if (num == 0) {
        return 1;
    } else {
        return num * calcularFactorial(num - 1);
    }
}

// Función para verificar si un número es primo
bool esPrimo(int num) {
    if (num <= 1) {
        return false;
    }
    for (int i = 2; i * i <= num; i++) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}

// Función para validar una cédula de ciudadanía colombiana (solo números)
bool validarCedulaColombiaNumeros(const char* cedula) {
    int longitud = strlen(cedula);
    if (longitud < 7 || longitud > 11) {
        return false;
    }
    for (int i = 0; i < longitud; i++) {
        if (!isdigit(cedula[i])) {
            return false;
        }
    }
    return true;
}

int main() {
    int opcionMenuPrincipal, opcionSubMenu, opcionSubmenu2;
    char respuesta;

    do {
        system("cls"); // Limpiar la pantalla en Windows

        cout << "MENU PRINCIPAL" << endl;
        cout << "1 - ESTRUCTURA DE DATOS" << endl;
        cout << "2 - VECTORES" << endl;
        cout << "3 - TERMINAR" << endl;
        cout << "INGRESE OPCION: ";
        cin >> opcionMenuPrincipal;
        cin.ignore(); // Ignorar el carácter de nueva línea

        if (cin.fail()) {
            cin.clear(); // Restaurar el estado del flujo de entrada
            cout << "Entrada no válida. Debe ingresar un número." << endl;
            continue; // Volver al menú principal
        }

        switch (opcionMenuPrincipal) {
            case 1:
                do {
                    system("cls"); // Limpiar la pantalla en Windows

                    cout << "ESTRUCTURA DE DATOS" << endl;
                    cout << "1 - OPERACIONES" << endl;
                    cout << "2 - VECTORES" << endl;
                    cout << "3 - TERMINAR" << endl;
                    cout << "INGRESE OPCION: ";
                    cin >> opcionSubMenu;
                    cin.ignore(); // Ignorar el carácter de nueva línea

                    if (cin.fail()) {
                        cin.clear(); // Restaurar el estado del flujo de entrada
                        cout << "Entrada no válida. Debe ingresar un número." << endl;
                        continue; // Volver al submenú 1
                    }

                    switch (opcionSubMenu) {
                        case 1: {
                            do {
                                system("cls"); // Limpiar la pantalla en Windows

                                cout << "OPERACIONES" << endl;
                                cout << "1 - VALIDACIONES" << endl;
                                cout << "2 - FACTORIAL" << endl;
                                cout << "3 - PARES E IMPARES" << endl;
                                cout << "4 - PRIMOS" << endl;
                                cout << "5 - RETORNAR" << endl;
                                cout << "INGRESE OPCION: ";
                                cin >> opcionSubmenu2;
                                cin.ignore(); // Ignorar el carácter de nueva línea

                                if (cin.fail()) {
                                    cin.clear(); // Restaurar el estado del flujo de entrada
                                    cout << "Entrada no válida. Debe ingresar un número." << endl;
                                    continue; // Volver al submenú 1
                                }

                                switch (opcionSubmenu2) {
                                    case 1: {
                                        char nombre[100];
                                        char cedula[12];
                                        int edad;
                                        char genero[10];
                                        cout << "Ingrese nombre completo: ";
                                        cin.ignore();
                                        cin.getline(nombre, sizeof(nombre));

                                        do {
                                            cout << "Ingrese numero de identificacion (solo números, 7 a 11 caracteres): ";
                                            cin.getline(cedula, sizeof(cedula));

                                            if (!validarCedulaColombiaNumeros(cedula)) {
                                                cout << "Cédula no válida. Debe tener entre 7 y 11 caracteres y contener solo números." << endl;
                                            }
                                        } while (!validarCedulaColombiaNumeros(cedula));

                                        cout << "Ingrese genero: ";
                                        cin.getline(genero, sizeof(genero));
                                        cout << "Ingrese edad: ";
                                        cin >> edad;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (edad < 18) {
                                            cout << "LA VACANTE ES SOLO PARA MAYORES DE EDAD" << endl;
                                        } else {
                                            cout << "HA SIDO REGISTRADO CORRECTAMENTE CON LOS SIGUIENTES DATOS" << endl;
                                            cout << "Nombre: " << nombre << endl;
                                            cout << "Identificacion: " << cedula << endl;
                                            cout << "Genero: " << genero << endl;
                                            cout << "Edad: " << edad << endl;
                                        }
                                        cout << "Pulse cualquier tecla para continuar";
                                        cin.get(); // Esperar la pulsación de una tecla
                                        break;
                                    }
                                    case 2: {
                                        int num;
                                        cout << "Ingrese un numero positivo de 1 dígito: ";
                                        cin >> num;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || num < 0 || num > 9) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Numero no válido. Debe ser un número positivo de 1 dígito." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 1
                                        }

                                        int factorial = calcularFactorial(num);
                                        cout << "RESULTADOS" << endl;
                                        cout << "El número leído es: " << num << endl;
                                        cout << "Su factorial es: " << factorial << endl;

                                        cout << "Desea calcular otro factorial (S/N): ";
                                        cin >> respuesta;
                                        cin.ignore(); // Ignorar el carácter de nueva línea
                                        break;
                                    }
                                    case 3: {
                                        int num;
                                        cout << "Ingrese un número positivo de 3 dígitos: ";
                                        cin >> num;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || num < 100 || num > 999) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Numero no válido. Debe ser un número positivo de 3 dígitos." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 1
                                        }

                                        if (num % 2 == 0) {
                                            cout << "RESULTADOS" << endl;
                                            cout << "El número leído es: " << num << endl;
                                            cout << "El número es par" << endl;
                                        } else {
                                            cout << "RESULTADOS" << endl;
                                            cout << "El número leído es: " << num << endl;
                                            cout << "El número es impar" << endl;
                                        }
                                        cout << "Desea verificar otro número (S/N): ";
                                        cin >> respuesta;
                                        cin.ignore(); // Ignorar el carácter de nueva línea
                                        break;
                                    }
                                    case 4: {
                                        int num;
                                        cout << "Ingrese un número positivo de 2 dígitos: ";
                                        cin >> num;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || num < 10 || num > 99) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Número no válido. Debe ser un número positivo de 2 dígitos." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 1
                                        }

                                        if (esPrimo(num)) {
                                            cout << "RESULTADOS" << endl;
                                            cout << "El número leído es: " << num << endl;
                                            cout << "El número es primo" << endl;
                                        } else {
                                            cout << "RESULTADOS" << endl;
                                            cout << "El número leído es: " << num << endl;
                                            cout << "El número no es primo" << endl;
                                        }
                                        cout << "Desea identificar otro número (S/N): ";
                                        cin >> respuesta;
                                        cin.ignore(); // Ignorar el carácter de nueva línea
                                        break;
                                    }
                                    case 5:
                                        break;
                                    default:
                                        cout << "LA OPCION INGRESADA NO ES VALIDA" << endl;
                                        break;
                                }
                            } while (opcionSubmenu2 != 5);
                            break;
                        case 2: {
                            do {
                                system("cls"); // Limpiar la pantalla en Windows

                                cout << "VECTORES" << endl;
                                cout << "1 - OPERACIONES EN EL MISMO VECTOR" << endl;
                                cout << "2 - NOTAS" << endl;
                                cout << "3 - OPERACIONES ENTRE VECTORES" << endl;
                                cout << "4 - ORDENAMIENTO" << endl;
                                cout << "5 - RETORNAR" << endl;
                                cout << "INGRESE OPCION: ";
                                cin >> opcionSubmenu2;
                                cin.ignore(); // Ignorar el carácter de nueva línea

                                if (cin.fail()) {
                                    cin.clear(); // Restaurar el estado del flujo de entrada
                                    cout << "Entrada no válida. Debe ingresar un número." << endl;
                                    continue; // Volver al submenú 2
                                }

                                switch (opcionSubmenu2) {
                                    case 1: {
                                        int vector[5];
                                        int sumatoria = 0;
                                        int productoria = 1;

                                        for (int i = 0; i < 5; i++) {
                                            cout << "Ingrese un número positivo de 1 dígito para la casilla " << i + 1 << ": ";
                                            cin >> vector[i];
                                            cin.ignore(); // Ignorar el carácter de nueva línea

                                            if (cin.fail() || vector[i] < 0 || vector[i] > 9) {
                                                cin.clear(); // Restaurar el estado del flujo de entrada
                                                cout << "Número no válido. Debe ser un número positivo de 1 dígito." << endl;
                                                cout << "Volviendo al submenú anterior..." << endl;
                                                break; // Volver al submenú 2
                                            }

                                            sumatoria += vector[i];
                                            productoria *= vector[i];
                                        }

                                        double media = static_cast<double>(sumatoria) / 5;

                                        cout << "Vector leído: ";
                                        for (int i = 0; i < 5; i++) {
                                            cout << vector[i];
                                            if (i < 4) {
                                                cout << ", ";
                                            }
                                        }
                                        cout << endl;
                                        cout << "Sumatoria: " << sumatoria << endl;
                                        cout << "Productoria: " << productoria << endl;
                                        cout << "Media: " << media << endl;

                                        cout << "Pulse cualquier tecla para continuar";
                                        cin.get(); // Esperar la pulsación de una tecla
                                        break;
                                    }
                                    case 2: {
                                        int N;
                                        cout << "Ingrese la cantidad de alumnos: ";
                                        cin >> N;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || N <= 0) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Entrada no válida. Debe ingresar un número entero positivo." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 2
                                        }

                                        struct Alumno {
                                            char nombre[100];
                                            double quiz;
                                            double trabajo;
                                            double parcial;
                                            double definitiva;
                                        };

                                        Alumno alumnos[N];

                                        cout << "Ingrese el nombre y las notas (Quiz, Trabajo y Parcial) de cada alumno:" << endl;

                                        for (int i = 0; i < N; i++) {
                                            cout << "Alumno " << i + 1 << " - Nombre: ";
                                            cin.ignore();
                                            cin.getline(alumnos[i].nombre, sizeof(alumnos[i].nombre));

                                            cout << "Alumno " << i + 1 << " - Nota Quiz: ";
                                            cin >> alumnos[i].quiz;

                                            if (cin.fail() || alumnos[i].quiz < 0 || alumnos[i].quiz > 5) {
                                                cin.clear();
                                                cout << "Nota Quiz no válida. Debe estar entre 0.0 y 5.0." << endl;
                                                cout << "Volviendo al ingreso de datos..." << endl;
                                                break;
                                            }

                                            cout << "Alumno " << i + 1 << " - Nota Trabajo: ";
                                            cin >> alumnos[i].trabajo;

                                            if (cin.fail() || alumnos[i].trabajo < 0 || alumnos[i].trabajo > 5) {
                                                cin.clear();
                                                cout << "Nota Trabajo no válida. Debe estar entre 0.0 y 5.0." << endl;
                                                cout << "Volviendo al ingreso de datos..." << endl;
                                                break;
                                            }

                                            cout << "Alumno " << i + 1 << " - Nota Parcial: ";
                                            cin >> alumnos[i].parcial;

                                            if (cin.fail() || alumnos[i].parcial < 0 || alumnos[i].parcial > 5) {
                                                cin.clear();
                                                cout << "Nota Parcial no válida. Debe estar entre 0.0 y 5.0." << endl;
                                                cout << "Volviendo al ingreso de datos..." << endl;
                                                break;
                                            }

                                            alumnos[i].definitiva = (alumnos[i].quiz * 0.25) + (alumnos[i].trabajo * 0.3) + (alumnos[i].parcial * 0.45);
                                        }

                                        cout << "Reporte de notas:" << endl;
                                        for (int i = 0; i < N; i++) {
                                            cout << "Alumno: " << alumnos[i].nombre << endl;
                                            cout << "Nota Quiz: " << alumnos[i].quiz << endl;
                                            cout << "Nota Trabajo: " << alumnos[i].trabajo << endl;
                                            cout << "Nota Parcial: " << alumnos[i].parcial << endl;
                                            cout << "Definitiva: " << alumnos[i].definitiva << endl;
                                        }

                                        cout << "Pulse cualquier tecla para continuar";
                                        cin.get(); // Esperar la pulsación de una tecla
                                        break;
                                    }
                                    case 3: {
                                        int N;
                                        cout << "Ingrese la cantidad de elementos para los vectores: ";
                                        cin >> N;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || N <= 0) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Entrada no válida. Debe ingresar un número entero positivo." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 2
                                        }

                                        int vector1[N];
                                        int vector2[N];
                                        int suma[N];
                                        int resta[N];
                                        int multiplicacion[N];
                                        double division[N];

                                        for (int i = 0; i < N; i++) {
                                            cout << "Ingrese un número positivo de 3 dígitos para la casilla " << i + 1 << " del primer vector: ";
                                            cin >> vector1[i];
                                            cin.ignore(); // Ignorar el carácter de nueva línea

                                            if (cin.fail() || vector1[i] < 100 || vector1[i] > 999) {
                                                cin.clear(); // Restaurar el estado del flujo de entrada
                                                cout << "Número no válido. Debe ser un número positivo de 3 dígitos." << endl;
                                                cout << "Volviendo al submenú anterior..." << endl;
                                                break; // Volver al submenú 2
                                            }

                                            cout << "Ingrese un número positivo de 1 dígito para la casilla " << i + 1 << " del segundo vector: ";
                                            cin >> vector2[i];
                                            cin.ignore(); // Ignorar el carácter de nueva línea

                                            if (cin.fail() || vector2[i] < 0 || vector2[i] > 9) {
                                                cin.clear(); // Restaurar el estado del flujo de entrada
                                                cout << "Número no válido. Debe ser un número positivo de 1 dígito." << endl;
                                                cout << "Volviendo al submenú anterior..." << endl;
                                                break; // Volver al submenú 2
                                            }

                                            suma[i] = vector1[i] + vector2[i];
                                            resta[i] = vector1[i] - vector2[i];
                                            multiplicacion[i] = vector1[i] * vector2[i];
                                            if (vector2[i] != 0) {
                                                division[i] = static_cast<double>(vector1[i]) / vector2[i];
                                            } else {
                                                division[i] = INFINITY; // División por cero
                                            }
                                        }

                                        cout << "RESULTADOS" << endl;
                                        cout << "VECTOR1\tVECTOR2\tSUMA\tRESTA\tMULTIPLICACIÓN\tDIVISIÓN" << endl;
                                        for (int i = 0; i < N; i++) {
                                            cout << vector1[i] << "\t" << vector2[i] << "\t" << suma[i] << "\t" << resta[i] << "\t" << multiplicacion[i] << "\t";
                                            if (division[i] == INFINITY) {
                                                cout << "Infinito" << endl;
                                            } else {
                                                cout << division[i] << endl;
                                            }
                                        }

                                        cout << "Desea realizar otras operaciones (S/N): ";
                                        cin >> respuesta;
                                        cin.ignore(); // Ignorar el carácter de nueva línea
                                        break;
                                    }
                                    case 4: {
                                        int N;
                                        cout << "Ingrese la cantidad de elementos para el vector: ";
                                        cin >> N;
                                        cin.ignore(); // Ignorar el carácter de nueva línea

                                        if (cin.fail() || N <= 0) {
                                            cin.clear(); // Restaurar el estado del flujo de entrada
                                            cout << "Entrada no válida. Debe ingresar un número entero positivo." << endl;
                                            cout << "Volviendo al submenú anterior..." << endl;
                                            break; // Volver al submenú 2
                                        }

                                        int vector[N];
                                        cout << "Ingrese " << N << " elementos para el vector:" << endl;

                                        for (int i = 0; i < N; i++) {
                                            cout << "Elemento " << i + 1 << ": ";
                                            cin >> vector[i];
                                            cin.ignore(); // Ignorar el carácter de nueva línea

                                            if (cin.fail() || vector[i] < 10 || vector[i] > 99) {
                                                cin.clear(); // Restaurar el estado del flujo de entrada
                                                cout << "Número no válido. Debe ser un número positivo de 2 dígitos." << endl;
                                                cout << "Volviendo al submenú anterior..." << endl;
                                                break; // Volver al submenú 2
                                            }
                                        }

                                        int opcionOrdenamiento;
                                        cout << "Vector leído: ";
                                        for (int i = 0; i < N; i++) {
                                            cout << vector[i];
                                            if (i < N - 1) {
                                                cout << ", ";
                                            }
                                        }
                                        cout << endl;

                                        do {
                                            cout << "¿Qué tipo de ordenamiento desea realizar?" << endl;
                                            cout << "1 - Ascendente" << endl;
                                            cout << "2 - Descendente" << endl;
                                            cout << "Ingrese la opción: ";
                                            cin >> opcionOrdenamiento;
                                            cin.ignore(); // Ignorar el carácter de nueva línea

                                            if (cin.fail() || (opcionOrdenamiento != 1 && opcionOrdenamiento != 2)) {
                                                cin.clear(); // Restaurar el estado del flujo de entrada
                                                cout << "Opción no válida. Debe elegir 1 o 2." << endl;
                                            }
                                        } while (cin.fail() || (opcionOrdenamiento != 1 && opcionOrdenamiento != 2));

                                        if (opcionOrdenamiento == 1) {
                                            for (int i = 0; i < N - 1; i++) {
                                                for (int j = 0; j < N - i - 1; j++) {
                                                    if (vector[j] > vector[j + 1]) {
                                                        swap(vector[j], vector[j + 1]);
                                                    }
                                                }
                                            }
                                            cout << "Vector ordenado Ascendentemente: ";
                                        } else {
                                            for (int i = 0; i < N - 1; i++) {
                                                for (int j = 0; j < N - i - 1; j++) {
                                                    if (vector[j] < vector[j + 1]) {
                                                        swap(vector[j], vector[j + 1]);
                                                    }
                                                }
                                            }
                                            cout << "Vector ordenado Descendentemente: ";
                                        }

                                        for (int i = 0; i < N; i++) {
                                            cout << vector[i];
                                            if (i < N - 1) {
                                                cout << ", ";
                                            }
                                        }
                                        cout << endl;

                                        cout << "Desea ordenar otro vector (S/N)? ";
                                        cin >> respuesta;
                                        cin.ignore(); // Ignorar el carácter de nueva línea
                                        break;
                                    }
                                    case 5:
                                        break;
                                    default:
                                        cout << "LA OPCION INGRESADA NO ES VALIDA" << endl;
                                        break;
                                }
                            } while (opcionSubmenu2 != 5);
                            break;
                        case 3:
                            break;
                        default:
                            cout << "LA OPCION INGRESADA NO ES VALIDA" << endl;
                            break;
                    }
                } while (opcionSubMenu != 3);
                break;
            case 3:
                cout << "Saliendo del programa..." << endl;
                break;
            default:
                cout << "LA OPCION INGRESADA NO ES VALIDA" << endl;
                break;
        }
    } while (opcionMenuPrincipal != 3);

    return 0;
}

