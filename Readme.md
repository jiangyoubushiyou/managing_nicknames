#�ص����ܵķ������˴��� 
socket.on('nickname', function (data, callback) {
        if (nicknames.indexOf(data) != -1) {
            callback(false);
        } else {
            callback(true);
            nicknames.push(data);
            socket.nickname = data;
            console.log('Nicknames are: ' + nicknames);
        }
    });
#�ص����ܵĿͻ��˴���
 jQuery(function ($) { 
        var nickName = $('#nickname');
        var setNicknameForm = $('#set-nickname');
        setNicknameForm.submit(function(event) {
          event.preventDefault(); 
          socket.emit('nickname', nickName.val(),function(data){
		  if(data){
			console.log('Nickname set successfully');
			setNicknameForm.hide();
			}else{
				setNicknameForm.prepend('<p>Sorry-that nickname is already taken.</p>');
			}
	  });
        });
      });