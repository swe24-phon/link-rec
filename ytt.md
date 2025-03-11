WORKDIR /app

COPY ./app/package*.json ./

RUN npm install

COPY ./app .

EXPOSE 5173

#CMD ["npm", "run", "dev"] CMD ["npm", "run", "dev", "--", "--host"]
FROM node:22
C:\Users\majic\AppData\Roaming\Ditto\Ditto.db
Foundations v2 - Part 2
Average: 65.82%

https://intranet.hbtn.io/concepts/952
code
pycodestyle’s documentation
https://pycodestyle.pycqa.org/en/latest/
ESLint
https://eslint.org/
https://en.wikipedia.org/wiki/Lint_(software)
https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
https://jsonplaceholder.typicode.com/
https://poe.com/
https://www.udemy.com/course/flutter-course-for-complete-beginners/
https://www.udemy.com/course/complete-network-hacking-course-2024-beginner-to-advanced/
https://www.udemy.com/course/learn-figma-uiux-design-masterclass-from-beginner-to-pro/
https://www.udemy.com/course/graphic-design-masterclass-master-illustrator-photoshop/
https://www.udemy.com/course/git-gitlab-github-fundamentals-for-software-developers/
https://www.udemy.com/course/build-11-javascript-application-and-web-javascript-bootcamp/
https://www.udemy.com/course/sales-funnel-mastery-build-design-and-automate-funnels/
https://www.udemy.com/course/programming-for-scientific-research/
https://www.udemy.com/course/mastering-django/
https://www.udemy.com/course/unreal-engine-5-learn-environment-art-for-video-games/
https://www.udemy.com/course/how-to-transition-to-product-management-and-succeed/
https://www.udemy.com/course/postgresql-bootcamp-complete-beginner-to-advanced-course/
https://www.udemy.com/course/user-experience-design-learn-ui-ux-app-design-with-figma/
mkdir pern-prisma-sqlite
cd pern-prisma-sqlite
npm init -y
npm init -y
npm install express cors prisma @prisma/client
npx prisma init
DATABASE_URL="file:./dev.db"
npx prisma generate
npx prisma migrate dev --name init
cd client
npm install dotenv
npx create-react-app client
cd client
npm install axios
cd ..
node server.js
// client/src/App.js

import React, { useEffect, useState } from 'react';
import axios from 'axios';

function App() {
  const [users, setUsers] = useState([]);
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [editingUserId, setEditingUserId] = useState(null);

  useEffect(() => {
    fetchUsers();
  }, []);

  const fetchUsers = async () => {
    try {
      const response = await axios.get(`${process.env.REACT_APP_API_URL}/api/users`, {
        headers: {
          'x-api-key': process.env.REACT_APP_API_KEY,
        },
      });
      setUsers(response.data);
    } catch (error) {
      console.error('Error fetching users:', error);
    }
  };

  const createUser = async () => {
    try {
      const response = await axios.post(
        `${process.env.REACT_APP_API_URL}/api/users`,
        { name, email },
        {
          headers: {
            'x-api-key': process.env.REACT_APP_API_KEY,
          },
        }
      );
      setUsers([...users, response.data]);
      setName('');
      setEmail('');
    } catch (error) {
      console.error('Error creating user:', error);
    }
  };

  const updateUser = async (id) => {
    try {
      const response = await axios.put(
        `${process.env.REACT_APP_API_URL}/api/users/${id}`,
        { name, email },
        {
          headers: {
            'x-api-key': process.env.REACT_APP_API_KEY,
          },
        }
      );
      setUsers(users.map((user) => (user.id === id ? response.data : user)));
      setName('');
      setEmail('');
      setEditingUserId(null); // Stop editing mode
    } catch (error) {
      console.error('Error updating user:', error);
    }
  };

  const deleteUser = async (id) => {
    try {
      await axios.delete(`${process.env.REACT_APP_API_URL}/api/users/${id}`, {
        headers: {
          'x-api-key': process.env.REACT_APP_API_KEY,
        },
      });
      setUsers(users.filter((user) => user.id !== id));
    } catch (error) {
      console.error('Error deleting user:', error);
    }
  };

  const handleEdit = (user) => {
    setName(user.name);
    setEmail(user.email);
    setEditingUserId(user.id);
  };

  return (
    <div className="App">
      <h1>User Management</h1>
      <div>
        <input
          type="text"
          placeholder="Name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <input
          type="email"
          placeholder="Email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
        {editingUserId ? (
          <button onClick={() => updateUser(editingUserId)}>Update User</button>
        ) : (
          <button onClick={createUser}>Create User</button>
        )}
      </div>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - {user.email}
            <button onClick={() => handleEdit(user)}>Edit</button>
            <button onClick={() => deleteUser(user.id
// client/src/App.js

import React, { useEffect, useState } from 'react';
import axios from 'axios';

function App() {
  const [users, setUsers] = useState([]);
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [editingUserId, setEditingUserId] = useState(null);

  useEffect(() => {
    fetchUsers();
  }, []);

  const fetchUsers = async () => {
    try {
      const response = await axios.get(`${process.env.REACT_APP_API_URL}/api/users`, {
        headers: {
          'x-api-key': process.env.REACT_APP_API_KEY,
        },
      });
      setUsers(response.data);
    } catch (error) {
      console.error('Error fetching users:', error);
    }
  };

  const createUser = async () => {
    try {
      const response = await axios.post(
        `${process.env.REACT_APP_API_URL}/api/users`,
        { name, email },
        {
          headers: {
            'x-api-key': process.env.REACT_APP_API_KEY,
          },
        }
      );
      setUsers([...users, response.data]);
      setName('');
      setEmail('');
    } catch (error) {
      console.error('Error creating user:', error);
    }
  };

  const updateUser = async (id) => {
    try {
      const response = await axios.put(
        `${process.env.REACT_APP_API_URL}/api/users/${id}`,
        { name, email },
        {
          headers: {
            'x-api-key': process.env.REACT_APP_API_KEY,
          },
        }
      );
      setUsers(users.map((user) => (user.id === id ? response.data : user)));
      setName('');
      setEmail('');
      setEditingUserId(null); // Stop editing mode
    } catch (error) {
      console.error('Error updating user:', error);
    }
  };

  const deleteUser = async (id) => {
    try {
      await axios.delete(`${process.env.REACT_APP_API_URL}/api/users/${id}`, {
        headers: {
          'x-api-key': process.env.REACT_APP_API_KEY,
        },
      });
      setUsers(users.filter((user) => user.id !== id));
    } catch (error) {
      console.error('Error deleting user:', error);
    }
  };

  const handleEdit = (user) => {
    setName(user.name);
    setEmail(user.email);
    setEditingUserId(user.id);
  };

  const handleCancelEdit = () => {
    setName('');
    setEmail('');
    setEditingUserId(null);
  };

  return (
    <div className="App">
      <h1>User Management</h1>
      <div>
        <input
          type="text"
          placeholder="Name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <input
          type="email"
          placeholder="Email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
        {editingUserId ? (
          <>
            <button onClick={() => updateUser(editingUserId)}>Update User</button>
            <button onClick={handleCancelEdit}>Cancel</button>
          </>
        ) : (
          <button onClick={createUser}>Create User</button>
        )}
      </div>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - {user.email}
            <button onClick={() => handleEdit(user)}>Edit</button>
            <button onClick={() => deleteUser(user.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
pp@pp.com
// server.js

const express = require('express');
const cors = require('cors');
const { PrismaClient } = require('@prisma/client');

const prisma = new PrismaClient();
const app = express();
const PORT = process.env.PORT || 3001;

app.use(cors());
app.use(express.json());

// Middleware for API key authentication
const apiKeyMiddleware = (req, res, next) => {
  const apiKey = req.headers['x-api-key'];
  if (apiKey !== 'your-api-key') {
    return res.status(401).json({ error: 'Unauthorized' });
  }
  next();
};

// Endpoint to get all users
app.get('/api/users', apiKeyMiddleware, async (req, res) => {
  try {
    const users = await prisma.user.findMany();
    res.json(users);
  } catch (error) {
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Endpoint to create a new user
app.post('/api/users', apiKeyMiddleware, async (req, res) => {
  const { name, email } = req.body;
  if (!name || !email) {
    return res.status(400).json({ error: 'Name and email are required' });
  }
  try {
    const user = await prisma.user.create({
      data: {
        name,
        email,
      },
    });
    res.status(201).json(user);
  } catch (error) {
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Endpoint to update a user
app.put('/api/users/:id', apiKeyMiddleware, async (req, res) => {
  const { id } = req.params;
  const { name, email } = req.body;
  try {
    const user = await prisma.user.update({
      where: { id: parseInt(id) },
      data: {
        name,
        email,
      },
    });
    res.json(user);
  } catch (error) {
    if (error.code === 'P2025') {
      return res.status(404).json({ error: 'User not found' });
    }
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Endpoint to delete a user
app.delete('/api/users/:id', apiKeyMiddleware, async (req, res) => {
  const { id } = req.params;
  try {
    const user = await prisma.user.delete({
      where: { id: parseInt(id) },
    });
    res.json(user);
  } catch (error) {
    if (error.code === 'P2025') {
      return res.status(404).json({ error: 'User not found' });
    }
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
# Node.js
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Prisma
prisma/dev.db

# React
client/node_modules/
client/npm-debug.log*
client/yarn-debug.log*
client/yarn-error.log*
client/build/

# Environment Variables
.env
client/.env

# macOS
.DS_Store

# VSCode
.vscode/
git rm --cached client
git add .
git commit -m "Initial commit"
git submodule deinit -f <submodule-path>

rm -rf .git/modules/<submodule-path>

git merge submodule-repo/main --allow-unrelated-histories

On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  (commit or discard the untracked or modified content in submodules)
        modified:   client (modified content, untracked content)

no changes added to commit (use "git add" and/or "git commit -a")
cd client
git add .
git commit -m "Committed changes in submodule"
cd ..

git reset client

git submodule deinit -f client
rm -rf .git/modules/client
rm -f .gitmodules

mv client/* ./
rm -rf client

git add .
git commit -m "Merged client submodule into main repository"

https://app.eraser.io/workspace/EsxbsS4v2g7Otkihy95b
https://github.com/meech-ward/Bun-Hono-React-Expense-Tracker
https://www.udemy.com/course/7-days-7-machine-learning-python-projects-from-scratch/
https://www.youtube.com/watch?v=M2Yg1kwPpts
https://www.youtube.com/watch?v=RKMaXcA0ISk
https://www.youtube.com/watch?v=lP6kLx_FCuc
https://youtu.be/ogdtB_m6G5g
https://youtu.be/tU_AXrvQjpo
https://youtu.be/V_NXT2-QIlE
https://www.youtube.com/watch?v=f8Z9JyB2EIE
https://www.youtube.com/watch?v=aAk3ORDr63U
https://www.youtube.com/watch?v=iUJ82_mVEVI
https://www.youtube.com/watch?v=9UIIMBqq1D4
https://www.youtube.com/watch?v=dNntYdZQ_mk
https://www.youtube.com/watch?v=wbj-DuaL748
https://www.youtube.com/watch?v=kC12OQZff_U
https://www.youtube.com/watch?v=g2DVt-k_CU8
https://www.youtube.com/watch?v=AHcBBx8CKys
https://www.youtube.com/watch?v=8i9WMD6xbuA
https://www.youtube.com/watch?v=1Jd_T_JXOtA
https://www.youtube.com/watch?v=I-E0EI9KMP0
https://www.youtube.com/watch?v=tqOs6MRdEfA
https://www.youtube.com/watch?v=QqoI5IcUJ50
https://www.youtube.com/watch?v=GdnUvshUqbE
https://www.youtube.com/watch?v=VenLRGHx3D4
https://www.youtube.com/watch?v=pfsaFV1os0o
https://www.youtube.com/watch?v=ky7ft0XkDAM
https://www.youtube.com/watch?v=32M1al-Y6Ag
https://www.youtube.com/watch?v=No0k-TMRuMA
https://www.youtube.com/watch?v=oIiv_335yus
https://youtu.be/Kf0q4Tf5M3c
https://www.youtube.com/watch?v=geujDzL0yXQ
