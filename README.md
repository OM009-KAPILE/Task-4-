1. What is Node.js ?
---Node.js is a runtime environment that lets you run JavaScript code outside of a web browser, mainly used to build servers and backend applications.



const http = require("http");
const url = require("url");

const server = http.createServer((req, res) => {
  // Parse URL
  const parsedUrl = url.parse(req.url, true);
  const path = parsedUrl.pathname;

  res.writeHead(200, { "Content-Type": "application/json" });

  // Different routes
  if (path === "/") {
    res.end(JSON.stringify({ message: "Hello, World!" }));
  } 
  else if (path === "/about") {
    res.end(JSON.stringify({ message: "This is a simple Node.js API using http" }));
  } 
  else if (path === "/students") {
    // Example array of students
    const students = [
      { name: "Alice", marks: 85 },
      { name: "Bob", marks: 67 },
      { name: "Charlie", marks: 92 }
    ];
    res.end(JSON.stringify({ students }));
  } 
  else if (path === "/highest") {
    // Calculate highest marks from array
    const marks = [45, 67, 89, 23, 99, 76];
    let max = marks[0];
    marks.forEach(m => {
      if (m > max) max = m;
    });
    res.end(JSON.stringify({ highestMarks: max }));
  } 
  else {
    // If route not found
    res.writeHead(404, { "Content-Type": "application/json" });
    res.end(JSON.stringify({ error: "Route not found" }));
  }
});

// Start server
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`✅ Server is running at http://localhost:${PORT}`);
});
