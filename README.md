# Investigación: Los 10 Hooks más usados de React (Vite + JavaScript)

React introdujo los Hooks para permitir el uso de estado y otras características del ciclo de vida en componentes funcionales. Al trabajar con un entorno rápido como Vite y JavaScript puro, estos son los 10 hooks fundamentales que dominan el desarrollo moderno:

## 1. useState
**Propósito:** Es el hook más básico y esencial. Permite declarar, leer y actualizar variables de estado dentro de un componente funcional.
* **Uso común:** Contadores, manejo de inputs en formularios, alternar visibilidad de modales (booleanos).
* **Ejemplo:** `const [count, setCount] = useState(0);`

## 2. useEffect
**Propósito:** Maneja los "efectos secundarios" en tus componentes, sincronizando tu componente con sistemas externos (APIs, DOM, suscripciones).
* **Uso común:** Hacer peticiones HTTP (`fetch`) de datos cuando el componente se monta (usando un arreglo de dependencias vacío `[]`).
* **Ejemplo:** `useEffect(() => { fetchData(); }, []);`

## 3. useContext
**Propósito:** Permite consumir valores de un "Contexto" de React sin tener que pasar *props* manualmente nivel por nivel a través del árbol de componentes (evita el *prop drilling*).
* **Uso común:** Manejo de temas (modo oscuro/claro), estado de autenticación del usuario o configuraciones globales y de idioma.
* **Ejemplo:** `const theme = useContext(ThemeContext);`

## 4. useRef
**Propósito:** Crea una referencia mutable que persiste durante todo el ciclo de vida del componente, pero, a diferencia de `useState`, **no** desencadena un re-renderizado cuando su valor cambia.
* **Uso común:** Acceder y manipular directamente un elemento del DOM (como hacer *focus* en un input) o guardar valores previos/temporales.
* **Ejemplo:** `const inputRef = useRef(null);`

## 5. useMemo
**Propósito:** Optimiza el rendimiento memorizando un valor calculado. Solo vuelve a ejecutar el cálculo si alguna de sus dependencias cambia.
* **Uso común:** Cálculos matemáticos pesados o filtrado/ordenamiento de listas grandes para evitar que se procesen en cada renderizado.
* **Ejemplo:** `const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);`

## 6. useCallback
**Propósito:** Similar a `useMemo`, pero diseñado específicamente para memorizar la definición de una función en lugar de un valor.
* **Uso común:** Pasar funciones como props a componentes hijos optimizados (envueltos en `React.memo`) para evitar que los hijos se re-rendericen innecesariamente.
* **Ejemplo:** `const memoizedCallback = useCallback(() => { doSomething(a, b); }, [a, b]);`

## 7. useReducer
**Propósito:** Una alternativa más robusta a `useState` para manejar lógicas de estado complejas, especialmente cuando el nuevo estado depende fuertemente del anterior o hay múltiples sub-valores interconectados.
* **Uso común:** Formularios con muchos campos, carritos de compras o emulación de arquitecturas tipo Redux a nivel local.
* **Ejemplo:** `const [state, dispatch] = useReducer(reducer, initialState);`

## 8. useLayoutEffect
**Propósito:** Su firma es idéntica a `useEffect`, pero se dispara de forma *síncrona* inmediatamente después de todas las mutaciones del DOM, antes de que el navegador pinte la pantalla.
* **Uso común:** Leer el diseño (layout) del DOM (como medir el tamaño o posición de un contenedor) y realizar ajustes sincrónicos para evitar parpadeos visuales (*flickering*).
* **Ejemplo:** `useLayoutEffect(() => { measureDOMElement(); }, []);`

## 9. useTransition
**Propósito:** Hook de concurrencia que permite marcar ciertas actualizaciones de estado como "transiciones" (de baja prioridad), manteniendo la interfaz de usuario fluida y receptiva durante actualizaciones pesadas.
* **Uso común:** Filtrado dinámico de listas masivas con un buscador o navegación entre pestañas complejas donde no quieres que la pantalla se congele.
* **Ejemplo:** `const [isPending, startTransition] = useTransition();`

## 10. useId
**Propósito:** Genera identificadores de cadenas únicos que son estables y consistentes entre el renderizado del servidor y el cliente.
* **Uso común:** Conectar atributos de accesibilidad (ARIA) en formularios (asociar un `<label>` con su `<input>` mediante el atributo `id` y `htmlFor`), asegurando que no haya colisiones si el componente se instancia múltiples veces en la misma vista.
* **Ejemplo:** `const id = useId();`

---
**💡 Nota sobre el entorno (Vite + JavaScript):** El uso de estos hooks es nativo de la biblioteca React. La ventaja fundamental de trabajar esta pila con **Vite** es su *Hot Module Replacement* (HMR) ultrarrápido. Durante el desarrollo, al modificar la lógica de tus hooks, Vite actualiza el módulo en el navegador en milisegundos y, en la mayoría de los casos, retiene el estado local (gracias a *React Refresh*), lo que hace que depurar hooks como `useState` o `useEffect` sea una experiencia sumamente ágil.
