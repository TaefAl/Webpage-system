# The idea 
The web page was created in a simple way and the SQL table was used to add personal information for the people entered in an easy way with the possibility of changing the private status

# The website 

<img width="2073" height="1032" alt="Image" src="https://github.com/user-attachments/assets/d19a0a5e-1638-4a3c-acee-d56bf09d865b" /> 

# Website preview 


# The Code

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Management System</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #0a0a0a, #1a1a1a);
            color: #e0e0e0;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(30, 30, 30, 0.9);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        h1 {
            text-align: center;
            color: #00d4ff;
            margin-bottom: 30px;
            font-size: 2.5em;
            text-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
        }

        .form-section {
            background: rgba(40, 40, 40, 0.8);
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .form-row {
            display: flex;
            gap: 20px;
            align-items: end;
            flex-wrap: wrap;
        }

        .form-group {
            flex: 1;
            min-width: 200px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #00d4ff;
            font-weight: bold;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            background: rgba(20, 20, 20, 0.8);
            color: #e0e0e0;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        input[type="text"]:focus, input[type="number"]:focus {
            outline: none;
            border-color: #00d4ff;
            box-shadow: 0 0 10px rgba(0, 212, 255, 0.3);
        }

        .submit-btn {
            padding: 12px 30px;
            background: linear-gradient(45deg, #00d4ff, #0099cc);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0, 212, 255, 0.4);
        }

        .table-section {
            background: rgba(40, 40, 40, 0.8);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        th {
            background: rgba(0, 212, 255, 0.1);
            color: #00d4ff;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        tr:hover {
            background: rgba(255, 255, 255, 0.05);
        }

        .status-active {
            color: #00ff88;
            font-weight: bold;
        }

        .status-inactive {
            color: #ff6b6b;
            font-weight: bold;
        }

        .toggle-btn {
            padding: 8px 16px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
            font-weight: bold;
            transition: all 0.3s ease;
            text-transform: uppercase;
        }

        .toggle-btn.active {
            background: linear-gradient(45deg, #ff6b6b, #ff4757);
            color: white;
        }

        .toggle-btn.inactive {
            background: linear-gradient(45deg, #00ff88, #00d68f);
            color: white;
        }

        .toggle-btn:hover {
            transform: scale(1.05);
        }

        .no-data {
            text-align: center;
            color: #888;
            font-style: italic;
            padding: 40px;
        }

        @media (max-width: 768px) {
            .form-row {
                flex-direction: column;
            }
            
            .form-group {
                min-width: 100%;
            }
            
            table {
                font-size: 14px;
            }
            
            th, td {
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Hello</h1>
        
        <div class="form-section">
            <form id="userForm">
                <div class="form-row">
                    <div class="form-group">
                        <label for="name">Name:</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="age">Age:</label>
                        <input type="number" id="age" name="age" min="1" max="120" required>
                    </div>
                    <div class="form-group">
                        <button type="submit" class="submit-btn">Submit</button>
                    </div>
                </div>
            </form>
        </div>

        <div class="table-section">
            <table id="userTable">
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Name</th>
                        <th>Age</th>
                        <th>Status</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody id="userTableBody">
                    <tr>
                        <td colspan="5" class="no-data">No users added yet. Use the form above to add users.</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <script>
        let users = [];
        let nextId = 1;

        const userForm = document.getElementById('userForm');
        const userTableBody = document.getElementById('userTableBody');
        const nameInput = document.getElementById('name');
        const ageInput = document.getElementById('age');

        // Handle form submission
        userForm.addEventListener('submit', function(e) {
            e.preventDefault();
            console.log('Form submitted');
            
            const name = nameInput.value.trim();
            const age = parseInt(ageInput.value);
            
            console.log('Name:', name, 'Age:', age);
            
            if (name && age && age > 0) {
                const newUser = {
                    id: nextId++,
                    name: name,
                    age: age,
                    status: 0 // Default to inactive (0)
                };
                
                console.log('New user created:', newUser);
                users.push(newUser);
                console.log('Users array:', users);
                
                renderTable();
                
                // Clear form
                nameInput.value = '';
                ageInput.value = '';
                nameInput.focus();
            } else {
                console.log('Validation failed');
                alert('Please fill in both name and age fields with valid values.');
            }
        });

        // Also try to handle button click directly as backup
        document.querySelector('.submit-btn').addEventListener('click', function(e) {
            e.preventDefault();
            console.log('Button clicked directly');
            
            const name = nameInput.value.trim();
            const age = parseInt(ageInput.value);
            
            if (name && age && age > 0) {
                const newUser = {
                    id: nextId++,
                    name: name,
                    age: age,
                    status: 0
                };
                
                users.push(newUser);
                renderTable();
                
                nameInput.value = '';
                ageInput.value = '';
                nameInput.focus();
            } else {
                alert('Please fill in both name and age fields with valid values.');
            }
        });

        // Render the user table
        function renderTable() {
            if (users.length === 0) {
                userTableBody.innerHTML = '<tr><td colspan="5" class="no-data">No users added yet. Use the form above to add users.</td></tr>';
                return;
            }

            userTableBody.innerHTML = users.map(user => `
                <tr>
                    <td>${user.id}</td>
                    <td>${user.name}</td>
                    <td>${user.age}</td>
                    <td class="${user.status === 1 ? 'status-active' : 'status-inactive'}">
                        ${user.status === 1 ? 'Active' : 'Inactive'}
                    </td>
                    <td>
                        <button class="toggle-btn ${user.status === 1 ? 'active' : 'inactive'}" 
                                onclick="toggleStatus(${user.id})">
                            ${user.status === 1 ? 'Deactivate' : 'Activate'}
                        </button>
                    </td>
                </tr>
            `).join('');
        }

        // Toggle user status
        function toggleStatus(userId) {
            const user = users.find(u => u.id === userId);
            if (user) {
                user.status = user.status === 1 ? 0 : 1;
                renderTable();
            }
        }

        // Initialize empty table
        renderTable();
    </script>
</body>
</html>

