<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pemesanan Jasuke Ghost</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f8f8;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #d63031;
            text-align: center;
            margin-bottom: 25px;
        }
        .food-item {
            margin-bottom: 20px;
        }
        .food-name {
            font-size: 24px;
            font-weight: bold;
            color: #d63031;
            margin-bottom: 5px;
        }
        .food-price {
            font-size: 18px;
            color: #e17055;
            margin-bottom: 15px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        textarea {
            height: 80px;
            resize: vertical;
        }
        .payment-options {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        .payment-option {
            flex: 1;
            text-align: center;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .payment-option.selected {
            border-color: #d63031;
            background-color: #ffecec;
        }
        .payment-option img {
            max-width: 100%;
            height: 60px;
            object-fit: contain;
        }
        .btn-order {
            background-color: #d63031;
            color: white;
            border: none;
            padding: 12px 20px;
            font-size: 18px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        .btn-order:hover {
            background-color: #b71c1c;
        }
        .ghost-icon {
            font-size: 30px;
            margin-right: 10px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1><span class="ghost-icon">👻</span>Pesan Jasuke Ghost</h1>
        
        <div class="food-item">
            <div class="food-name">Jasuke Ghost</div>
            <div class="food-price">Rp 12.000</div>
        </div>
        
        <form id="orderForm">
            <div class="form-group">
                <label for="spicy-level">Level Pedas:</label>
                <select id="spicy-level" required>
                    <option value="">Pilih level pedas</option>
                    <option value="Pedas">Pedas</option>
                    <option value="Extra Pedas">Extra Pedas</option>
                    <option value="Ghost">Ghost (Paling Pedas!)</option>
                </select>
            </div>
            
            <div class="form-group">
                <label>Metode Pembayaran:</label>
                <div class="payment-options">
                    <div class="payment-option" onclick="selectPayment('qris')">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/QR_code_for_mobile_English_Wikipedia.svg/1200px-QR_code_for_mobile_English_Wikipedia.svg.png" alt="QRIS">
                        <div>QRIS</div>
                    </div>
                    <div class="payment-option" onclick="selectPayment('cash')">
                        <img src="https://cdn-icons-png.flaticon.com/512/2703/2703544.png" alt="Cash">
                        <div>Cash</div>
                    </div>
                </div>
                <input type="hidden" id="payment-method" required>
            </div>
            
            <div class="form-group">
                <label for="notes">Catatan (Opsional):</label>
                <textarea id="notes" placeholder="Contoh: Kurangi garam, tambah keju, dll."></textarea>
            </div>
            
            <button type="button" class="btn-order" onclick="placeOrder()">Pesan Sekarang</button>
        </form>
    </div>

    <script>
        function selectPayment(method) {
            document.getElementById('payment-method').value = method;
            
            // Update UI
            const options = document.querySelectorAll('.payment-option');
            options.forEach(option => {
                option.classList.remove('selected');
            });
            
            event.currentTarget.classList.add('selected');
        }
        
        function placeOrder() {
            const spicyLevel = document.getElementById('spicy-level').value;
            const paymentMethod = document.getElementById('payment-method').value;
            const notes = document.getElementById('notes').value;
            
            // Validasi
            if (!spicyLevel || !paymentMethod) {
                alert('Harap pilih level pedas dan metode pembayaran!');
                return;
            }
            
            // Format pesan untuk WhatsApp
            let message = `Halo, saya ingin memesan Jasuke Ghost dengan detail berikut:%0A%0A`;
            message += `*Level Pedas:* ${spicyLevel}%0A`;
            message += `*Metode Pembayaran:* ${paymentMethod.toUpperCase()}%0A`;
            
            if (notes) {
                message += `*Catatan:* ${notes}%0A`;
            }
            
            message += `%0ATotal: *Rp 12.000*%0A%0ATerima kasih!`;
            
            // Redirect ke WhatsApp
            window.open(`https://wa.me/6281227858684?text=${message}`, '_blank');
        }
    </script>
</body>
</html><!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pemesanan Jasuke Ghost</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f8f8;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #d63031;
            text-align: center;
            margin-bottom: 25px;
        }
        .food-item {
            margin-bottom: 20px;
        }
        .food-name {
            font-size: 24px;
            font-weight: bold;
            color: #d63031;
            margin-bottom: 5px;
        }
        .food-price {
            font-size: 18px;
            color: #e17055;
            margin-bottom: 15px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        textarea {
            height: 80px;
            resize: vertical;
        }
        .payment-options {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        .payment-option {
            flex: 1;
            text-align: center;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .payment-option.selected {
            border-color: #d63031;
            background-color: #ffecec;
        }
        .payment-option img {
            max-width: 100%;
            height: 60px;
            object-fit: contain;
        }
        .btn-order {
            background-color: #d63031;
            color: white;
            border: none;
            padding: 12px 20px;
            font-size: 18px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        .btn-order:hover {
            background-color: #b71c1c;
        }
        .ghost-icon {
            font-size: 30px;
            margin-right: 10px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1><span class="ghost-icon">👻</span>Pesan Jasuke Ghost</h1>
        
        <div class="food-item">
            <div class="food-name">Jasuke Ghost</div>
            <div class="food-price">Rp 12.000</div>
        </div>
        
        <form id="orderForm">
            <div class="form-group">
                <label for="spicy-level">Level Pedas:</label>
                <select id="spicy-level" required>
                    <option value="">Pilih level pedas</option>
                    <option value="Pedas">Pedas</option>
                    <option value="Extra Pedas">Extra Pedas</option>
                    <option value="Ghost">Ghost (Paling Pedas!)</option>
                </select>
            </div>
            
            <div class="form-group">
                <label>Metode Pembayaran:</label>
                <div class="payment-options">
                    <div class="payment-option" onclick="selectPayment('qris')">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/QR_code_for_mobile_English_Wikipedia.svg/1200px-QR_code_for_mobile_English_Wikipedia.svg.png" alt="QRIS">
                        <div>QRIS</div>
                    </div>
                    <div class="payment-option" onclick="selectPayment('cash')">
                        <img src="https://cdn-icons-png.flaticon.com/512/2703/2703544.png" alt="Cash">
                        <div>Cash</div>
                    </div>
                </div>
                <input type="hidden" id="payment-method" required>
            </div>
            
            <div class="form-group">
                <label for="notes">Catatan (Opsional):</label>
                <textarea id="notes" placeholder="Contoh: Kurangi garam, tambah keju, dll."></textarea>
            </div>
            
            <button type="button" class="btn-order" onclick="placeOrder()">Pesan Sekarang</button>
        </form>
    </div>

    <script>
        function selectPayment(method) {
            document.getElementById('payment-method').value = method;
            
            // Update UI
            const options = document.querySelectorAll('.payment-option');
            options.forEach(option => {
                option.classList.remove('selected');
            });
            
            event.currentTarget.classList.add('selected');
        }
        
        function placeOrder() {
            const spicyLevel = document.getElementById('spicy-level').value;
            const paymentMethod = document.getElementById('payment-method').value;
            const notes = document.getElementById('notes').value;
            
            // Validasi
            if (!spicyLevel || !paymentMethod) {
                alert('Harap pilih level pedas dan metode pembayaran!');
                return;
            }
            
            // Format pesan untuk WhatsApp
            let message = `Halo, saya ingin memesan Jasuke Ghost dengan detail berikut:%0A%0A`;
            message += `*Level Pedas:* ${spicyLevel}%0A`;
            message += `*Metode Pembayaran:* ${paymentMethod.toUpperCase()}%0A`;
            
            if (notes) {
                message += `*Catatan:* ${notes}%0A`;
            }
            
            message += `%0ATotal: *Rp 12.000*%0A%0ATerima kasih!`;
            
            // Redirect ke WhatsApp
            window.open(`https://wa.me/6281227858684?text=${message}`, '_blank');
        }
    </script>
</body>
</html>
