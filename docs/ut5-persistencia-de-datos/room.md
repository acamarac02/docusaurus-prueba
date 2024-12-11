# Acceso a base de datos con Room
**Room** es una biblioteca de **persistencia de datos** para Android que forma parte de Android Jetpack. Proporciona una capa de abstracción sobre SQLite, lo que facilita la creación, lectura, actualización y eliminación de datos en una base de datos local.

---

## **Características principales de Room**
1. **Simplificación de SQLite**:
   - Automatiza tareas repetitivas como la creación de consultas o manejo de esquemas.
   - Usa anotaciones para definir tablas, columnas y relaciones.

2. **Tipos de componentes clave**:
   - **Entity**: Representa una tabla en la base de datos.
   - **DAO (Data Access Object)**: Define métodos para interactuar con la base de datos (consultas, inserciones, actualizaciones, eliminaciones).
   - **Database**: Es el punto de entrada principal que vincula entidades y DAOs.

3. **Integración con LiveData y Flow**:
   - Permite observar cambios en los datos de forma reactiva, ideal para la arquitectura MVVM.

4. **Validación de esquemas en tiempo de compilación**:
   - Reduce errores comunes al validar estructuras y consultas durante el desarrollo.

5. **Compatibilidad con migraciones de base de datos**:
   - Facilita actualizaciones de la estructura de la base de datos sin perder datos existentes.

---

### **Ventajas de usar Room**
- Código más limpio y menos propenso a errores.
- Manejo automático de consultas y actualizaciones.
- Soporte integrado para programación reactiva.
- Mejor integración con otras bibliotecas de Android Jetpack.

---

:::tip[My tip]

Use this awesome feature option

:::

## Ejemplo básico
1. **Definir una entidad**:
   ```jsx kotlin title="src/components/HelloDocusaurus.js"
   @Entity
   data class User(
       @PrimaryKey val id: Int,
       val name: String,
       val age: Int
   )
   ```

:::danger[Cuidado!!]

This action is dangerous

:::

:::warning[Cuidadito]

This action is dangerous

:::

:::info[Extra info]

This action is dangerous

:::

2. **Crear un DAO**:
   ```kotlin
   @Dao
   interface UserDao {
       @Query("SELECT * FROM User")
       fun getAllUsers(): List<User>

       @Insert
       fun insertUser(user: User)
   }
   ```

3. **Configurar la base de datos**:
   ```kotlin
   @Database(entities = [User::class], version = 1)
   abstract class AppDatabase : RoomDatabase() {
       abstract fun userDao(): UserDao
   }
   ```

4. **Inicializar Room**:
   ```kotlin
   val db = Room.databaseBuilder(
       applicationContext,
       AppDatabase::class.java, "database-name"
   ).build()
   ```

---

Room es una opción robusta y moderna para manejar bases de datos en aplicaciones Android, simplificando el trabajo y reduciendo errores. 😊