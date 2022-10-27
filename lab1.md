![задание](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5.png)

Вид окон в системе:
окно регистрации:
![окно регистрации](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
окно входа:
![окно входа](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B2%D1%82%D0%BE%D1%80%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
окно восстановления пароля:
![окно восстановления пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D1%82%D1%80%D0%B5%D1%82%D0%B8%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
окно смены пароля:
![окно смены пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D1%87%D0%B5%D1%82%D0%B2%D0%B5%D1%80%D1%82%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
главная страница:
![главная страница](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%BF%D1%8F%D1%82%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)

Возможные пользовательские сценарии:
1)Регистрация:
пользователь заходит на сайт регистрации, вводит логин и пароль с его повторением. После чего пароль и логин записываются в базу данных, а пользователя переносят на страницу входа.
2)Вход:
пользователь вводит логин и пароль, они проверяются в базе данных, и пользователя переносят на главную страницу.
3)Восстановление пароля:
пользователь нажимает на кнопку "восстановить", после этого его переносят на страницу восстановления пароля, где он вводит свой логин и новый пароль, после чего у него меняется пароль.
4)смена пароля: пользователь на главной странице нажимает на кнопку "сменить пароль", после чего его переносят на страницу смены пароля, где пользователь вводит старый пароль и новый с его повторением, после чего пароль сменяется.

Примеры запросов на сервер и ответы на них:
![успешный вход](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(1).png)
![успешный выход](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(2).png)
![безуспешная попытка перехода к профилю](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(3).png)
![смена пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(4).png)
![восстановление пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(5).png)
![безуспешная регистрация](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(6).png)
![успешная регистрация](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled.png)

Работа сайта на примере блок схемы (алгоритмы использующиеся на сайте):
![блок схема сайта](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B1%D0%BB%D0%BE%D0%BA%20%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D0%BB%D1%80-1%20%D0%BE%D0%BF.png)

База данных, использующаяся сайтом - это mySQL. Состоит таблица базы данных из 3 столбцов:
1)id  2)login  3)password.

Основные фрагменты кода:
1)код регистрации:
```sh
    $login = $_POST['login'];
    $password = $_POST['password'];
    $password_confirm = $_POST['password_confirm'];
	
	$number = preg_match('@[0-9]@', $password);
	$lowercase = preg_match('@[a-z]@', $password);
	if($login === ""){
		$_SESSION['message'] = 'придумайте логин';
		header('Location: ../register.php');
	}
 
	if(strlen($password) < 4 || !$number || !$lowercase) {
		$_SESSION['message'] = 'В пароля должна быть цифра и буква, его длина должна быть больше 4';
		header('Location: ../register.php');
	}
	else{

    if ($password === $password_confirm) {

		$password = $password . 2**strlen($password);
        $password = md5($password);

        mysqli_query($connect, "INSERT INTO `user` (`id`, `login`, `password`) VALUES (NULL, '$login', '$password')");

        $_SESSION['message'] = 'Регистрация прошла успешно!';
        header('Location: ../index.php');


    } else {
        $_SESSION['message'] = 'Пароли не совпадают';
        header('Location: ../register.php');
    }
```
2)код авторизации:
```sh
    $login = $_POST['login'];
    $password = $_POST['password'];
	$password = $password . 2**strlen($password);
    $password = md5($password);

    $check_user = mysqli_query($connect, "SELECT * FROM `user` WHERE `login` = '$login' AND `password` = '$password'");
    if (mysqli_num_rows($check_user) > 0) {

        $user = mysqli_fetch_assoc($check_user);

        $_SESSION['user'] = [
            "id" => $user['id']
        ];

        header('Location: ../profile.php');

    } else {
        $_SESSION['message'] = 'Не верный логин или пароль';
        header('Location: ../index.php');
    }
```
3)код смены пароля:
```sh
$id = $_SESSION['user']['id']; // id юзера из сессии
	$query = "SELECT * FROM user WHERE id='$id'";
	
	$result = mysqli_query($connect, $query);
	$user = mysqli_fetch_assoc($result);
	
	$hash = $user['password']; // соленый пароль из БД
	$password = $_POST['password'];
	$password = $password . 2**strlen($password);
    $password = md5($password);
	$newpassword = $_POST['new_password'];
	$newpassword = $newpassword . 2**strlen($newpassword);
    $newpassword = md5($newpassword);
	
	// Проверяем соответствие хеша из базы введенному старому паролю
	if ($password === $hash) {
		
		$query = "UPDATE user SET password='$newpassword' WHERE id='$id'";
		mysqli_query($connect, $query);
		$_SESSION['message'] = 'Пароль сменен';
		header('Location: ../changePassword.php');
	} else {
		$_SESSION['message'] = 'Старый пароль не верен';
        header('Location: ../changePassword.php');
		// старый пароль введен неверно, выведем сообщение
	}
```