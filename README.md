# New-Internet-Programming-Project
Abaout SDG 3 Good Health &amp; Well Being (db.php)

<?php
// db.php - PDO connection for XAMPP
declare(strict_types=1);

$DB_HOST = '127.0.0.1';
$DB_NAME = 'bts4733_health';
$DB_USER = 'root';
$DB_PASS = ''; // default XAMPP blank. Change if you use a password.
$DB_DSN  = "mysql:host=$DB_HOST;dbname=$DB_NAME;charset=utf8mb4";

$options = [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_EMULATE_PREPARES => false,
];

try {
    $pdo = new PDO($DB_DSN, $DB_USER, $DB_PASS, $options);
} catch (PDOException $e) {
    // In production, do not expose details. For student project we show it.
    http_response_code(500);
    header('Content-Type: application/json');
    echo json_encode(['error' => 'DB connection failed', 'detail' => $e->getMessage()]);
    exit;
}
