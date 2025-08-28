// Import Node's built-in http module
const http = require("http");

// Sample data (students)
const students = [
  { id: 1, name: "Om", marks: 85 },
  { id: 2, name: "Aarav", marks: 92 },
  { id: 3, name: "Riya", marks: 78 }
];

// Create server
const server = http.createServer((req, res) => {
  res.setHeader("Content-Type", "application/json");

  if (req.url === "/" && req.method === "GET") {
    res.writeHead(200);
    res.end(JSON.stringify({ message: "Hello, World!" }));
  } 
  else if (req.url === "/students" && req.method === "GET") {
    res.writeHead(200);
    res.end(JSON.stringify(students));
  } 
  else {
    res.writeHead(404);
    res.end(JSON.stringify({ error: "Not Found" }));
  }
});

// Start server
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`✅ Server running at http://localhost:${PORT}`);
});
