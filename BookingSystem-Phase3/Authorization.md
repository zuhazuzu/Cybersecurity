In this task, i had to reinstall VirtualBox (my kali linux was somehow in start/stop loop, brobably reboot would have been sufficient)

user 1: 123@mail.com 
user 2: 234@mail.com
admin 1: admin1@mail.com

I did not found specific way for admin to remove reservations. other parts (1,2,3,4,5,7 and 8) were present.

| Page/Feature            | Guest | Reserver | Administrator |
| :---------------------- | :---: | :------: | :-----------: |
| `/` (index)             |       |          |               |
| └── View resource form  |   ✅   |    ✅     |       ✅       |
| └── Create new resource |   ❌   |    ✅     |       ✅       |

Users can go to web page.


| `/resources`            | Guest | Reserver | Administrator |
| :---------------------- | :---: | :------: | :-----------: |
| └── Create new resource |  ✅*1  |    ✅     |       ✅       |
1. Guest can add resources when entering  correct URL
2. Adminstrator can edit resource bu not delete them

| `/reservation`       | Guest | Reserver | Administrator |
| :------------------- | :---: | :------: | :-----------: |
| └── add reservations |  ❌*1  |   ✅*2    |       ✅       |
1. Guest cannot enter site, gets "unauthorized"
2. if user is too young they cannot make reservations.
3. When adding second reservation user gets *new row for relation "zephyr_reservations" violates check constraint "zephyr_reservations_check"* Brobably user can't have multiple reservations at same time table. even if reservations are with different resources.

| `/reservation?id=1` (1st reservation. won't include all) | Guest | Reserver | Administrator |
| :------------------------------------------------------- | :---: | :------: | :-----------: |
| └── Edit reservations                                    |  ❌*1  |  ✅*2,3   |      ✅*2      |
1. Guest cannot enter site, gets "unauthorized"
2. Each reserver and admin can edit each other reservers and admins reservations in any way.
3. When reserver edits reservation, edited reservation bolds it and any reservar can enter reservations page via UI.


| `/register`         | Guest | Reserver | Administrator |
| :------------------ | :---: | :------: | :-----------: |
| └── create new user |   ✅   |    ✅     |       ✅       |

Everyone can enter register page, but Reserver and Admin have to navigate via URL navigation.

| `/login`              | Guest | Reserver | Administrator |
| :-------------------- | :---: | :------: | :-----------: |
| └── Enter crecendials |   ✅   |   ✅*1    |      ✅*1      |
1. Reserver and admin can enter login via URL page and login as another user or admin.

| `/logout`    | Guest | Reserver | Administrator |
| :----------- | :---: | :------: | :-----------: |
| └──can enter |   ✅   |    ✅     |       ✅       |

Guest has to enter here via URL, others can do it also by UI button

| `/http://localhost:8000/api/users | Guest | Reserver | Administrator |
| :-------------------------------- | :---: | :------: | :-----------: |
| └──can enter                      |   ✅   |    ✅     |       ✅       |

All can enter via URL and see 1: user token., 2: user name and 3: role

| `http://localhost:8000/api/resources | Guest | Reserver | Administrator |
| :----------------------------------- | :---: | :------: | :-----------: |
| └──can enter                         |   ✅   |    ✅     |       ✅       |

All can see information in here when entering correct ULR

| `http://localhost:8000/api/session | Guest | Reserver | Administrator |
| :--------------------------------- | :---: | :------: | :-----------: |
| └──can enter                       |   ✅   |    ✅     |       ✅       |

All can enter page and whoever is in page, gets corresponding response from site
1. user gets "unauthorized"
2. reserver and admin gets their email and role.

| `http://localhost:8000/api/reservations/1 | Guest | Reserver | Administrator |
| :---------------------------------------- | :---: | :------: | :-----------: |
| └──can enter                              |   ✅   |    ✅     |       ✅       |

reservation and corresponding ID (here is 1) shows information about reservation.

| `http://localhost:8000/static/reservationsForm.js | Guest | Reserver | Administrator |
| :------------------------------------------------ | :---: | :------: | :-----------: |
| └──can enter                                      |   ✅   |    ✅     |       ✅       |

When entering, who ever enters gets to see contents of this file. 

| `http://localhost:8000/static/resourceForm.js | Guest | Reserver | Administrator |
| :-------------------------------------------- | :---: | :------: | :-----------: |
| └──can enter                                  |   ✅   |    ✅     |       ✅       |

When entering, who ever enters gets to see contents of this file. 

| `http://localhost:8000/static/tailwind.css | Guest | Reserver | Administrator |
| :----------------------------------------- | :---: | :------: | :-----------: |
| └──can enter                               |   ✅   |    ✅     |       ✅       |

When entering, who ever enters gets to see contents of this file. 