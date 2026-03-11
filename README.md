<img width="1223" height="897" alt="image" src="https://github.com/user-attachments/assets/32fea5e5-83e9-45c7-808d-ff201e933d84" />
<br>
//1
enum UserRole {
    Admin = "ADMIN",
    Teacher = "TEACHER",
    Student = "STUDENT"
}

//2
interface User {
    id: number;
    name: string;
    role: UserRole;
    email?: string;
}
//3
function printUserInfo(user: User): void {
    console.log(`ID: ${user.id}, Имя: ${user.name}, Роль: ${user.role}`);
    
    if (user.role === UserRole.Admin) {
        console.log("Доступ: Полный административный контроль.");
    }
}
//4
const users: User[] = [
    { id: 1, name: "Алексей", role: UserRole.Admin },
    { id: 2, name: "Мария", role: UserRole.Teacher },
    { id: 3, name: "Иван", role: UserRole.Student },
    { id: 4, name: "Елена", role: UserRole.Student }
];

console.log("Все пользователи:");
users.forEach(u => printUserInfo(u));

const studentsOnly = users.filter(u => u.role === UserRole.Student);
console.log("Список студентов:", studentsOnly);
//5
function crateUser(id: number, name: string, role: UserRole, age?: number): User {
    const newUser: User = { id, name, role };
    if (age) {
    console.log(`${name} - указал возраст: ${age}`);
    }
    return newUser;
}
const userWithAge = crateUser(5, "Дмитрий", UserRole.Student, 20);
const userWithoutAge = crateUser(6, "Анна", UserRole.Teacher);
