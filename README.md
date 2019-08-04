# Send-email-from-google-acccount
How to integrate email and send from your google account

#1 Get to your Gmail account's security settings and set permissions for "Less secure apps" to Enabled.

#2 Use below function to configure email

function send_email($to_email,$subject,$body){
            //Create a new PHPMailer instance
            $mail = new PHPMailer;
            //Tell PHPMailer to use SMTP
            $mail->isSMTP();
            //Enable SMTP debugging
            // 0 = off (for production use)
            // 1 = client messages
            // 2 = client and server messages
            $mail->SMTPDebug = 0;
            //Set the hostname of the mail server
            $mail->Host = 'smtp.gmail.com';
            //$mail->Host = 'tls://smtp.gmail.com:587';
            // use
            //$mail->Host = gethostbyname('smtp.gmail.com');
            // if your network does not support SMTP over IPv6
            //Set the SMTP port number - 587 for authenticated TLS, a.k.a. RFC4409 SMTP submission
            $mail->Port = 587;
            $mail->IsHTML = true;
            //Set the encryption system to use - ssl (deprecated) or tls
            //$mail->SMTPSecure = 'tls';
            //Whether to use SMTP authentication
            $mail->SMTPAuth = true;
            //Username to use for SMTP authentication - use full email address for gmail
            $mail->Username = "XXXXX@gmail.com";
            //Password to use for SMTP authentication
            $mail->Password = "XXXXXXXX";
            //Set who the message is to be sent from
            $mail->setFrom('XXXXXXXX');
            //Set an alternative reply-to address
            $mail->addReplyTo('replyto@example.com');
            //Set who the message is to be sent to
            $mail->addAddress($to_email);
            //Set the subject line
            $mail->Subject = $subject;
            //Read an HTML message body from an external file, convert referenced images to embedded,
            //convert HTML into a basic plain-text alternative body
            $mail->msgHTML($body);
            //Replace the plain text body with one created manually
            $mail->Body = $body;
            //$mail->AltBody = 'This is a plain-text message body';
            //send the message, check for errors
            if (!$mail->send()) {
                echo "Mailer Error: " . $mail->ErrorInfo;
            } else {
                echo "Message sent!";
            }
            return true;
    }
    
#3 echo $testemail = send_email("nileshpatil@XXX.com","Test Subject","Test body!");
