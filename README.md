# Super Dolores 🏪💬💰🚕

SuperApp didáctica de Dolores Hidalgo: **Mensajería, Pagos, Comercio y Transporte** en un solo ecosistema,
construida con TDD siguiendo el *Manual paso a paso con TDD — Super Dolores* (Desarrollo Móvil Integral, UTNG).

> ⚠️ Simulación educativa: no mueve dinero real ni transporta personas. Todo vive en memoria.

## Cómo correrlo

1. Abre esta carpeta en VS Code.
2. Genera las carpetas de Android/iOS/Web (no borra tu código):

   ```
   flutter create --project-name super_dolores .
   ```

3. **Borra `test/widget_test.dart`** si `flutter create` lo generó (prueba un `MyApp` que no existe y saldría en rojo).
4. Descarga dependencias y corre las pruebas:

   ```
   flutter pub get
   flutter test
   ```

5. Ejecuta la app: `flutter run`

## Estructura

```
lib/
  dominio/            <- reglas del negocio (Dart puro, sin Flutter)
    dinero  excepciones  eventos  monedero
    mensajeria  comercio  transporte
    mini_app  contexto  plataforma
    lealtad  analitica  notificaciones  sugerencias
  presentacion/
    vm/         inicio  monedero  chat  tienda  viajes  metricas
    pantallas/  inicio  monedero  chat  tienda  viajes  metricas  horoscopo  widgets
  main.dart     <- la "concha" (shell) de la SuperApp
test/
  dominio_test.dart  servicios_test.dart  retencion_test.dart  vms_test.dart
```

## Qué probar en la app

- Cambiar de persona (Ana, Luis, Marta) con el botón de arriba a la derecha en Inicio.
- Enviar dinero desde el chat (botón **$**) y ver que cambian ambos saldos.
- Comprar en la tortillería y ver la comisión del 5%.
- Pedir un viaje y avanzar sus estados; los saltos ilegales muestran un aviso.
- Abrir la mini-app de Horóscopo (tercero) y ver que no puede leer saldo ni chats.
- Apagar Viajes con el kill switch: desaparece de la barra.
- Tablero de retención con datos simulados (DAU, WAU, MAU, stickiness, D1/D7).

## Ciclo rojo → verde

Para una captura en **rojo**, cambia temporalmente una regla (por ejemplo, en `lib/dominio/dinero.dart`
haz que `porcentaje` devuelva `0`) y corre `flutter test`. Regrésala a como estaba y vuelve a correr
las pruebas para la captura en **verde**.
