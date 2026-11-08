```javascript
// ==============================================================
// =====================HOME BUTTONS=============================
// ==============================================================
var statusInfo = ''; // This va
var currentCoaster = 0;

var coasterInfo = [
  {
    'Maxx Force':{
      'id': 1,
      'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/348s.jpg',
      'message': 'The ride won\'t open immediately. If you see more than 20 people, go to the next ride.'
  }
  },
  {
    'Sky Striker': {
      'id': 2,
      'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/images.jpeg',
      'message': 'You do NOT want to wait more than 40 minutes for this ride.'
  }
    },
  {
    'Goliath': {
      'id': 3,
      'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/rdpyv92t5q4f1.jpeg',
      'message': 'This line moves VERY slow; get on it early.'
  }
  },
  {
    'Raging Bull': {
      'id': 4,
      'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/images-2.jpeg',
      'message': 'This line should fill up mid-day, but it moves fast.'
    }
}];

function setCoasterScreen(id){
  id = (typeof id !== 'undefined') ? id : 1;
  var singleCoasterInfo = {};
  
  for (var i = 0; i < coasterInfo.length; i++) {
    var coasterName = Object.keys(coasterInfo[i])[0];
    if (coasterInfo[i][coasterName].id === id) {
      singleCoasterInfo = coasterInfo[i][coasterName];
      singleCoasterInfo.name = coasterName;
      break;
    }
  }
  currentCoaster = singleCoasterInfo ? id : 0;
  setProperty('rideName', 'text', singleCoasterInfo.name);
  setProperty('rideImage', 'image', singleCoasterInfo.image);
  setProperty('rideMessage', 'text', singleCoasterInfo.message);
  playSound("assets/category_bell/notification_4.mp3");
}

function nextCoaster(){
  if (currentCoaster <= 3 && currentCoaster >= 1) setCoasterScreen(currentCoaster+1);
  else if (currentCoaster == 4) setScreen('ropeDropScreen');
}

function previousCoaster(){
  if (currentCoaster <= 4 && currentCoaster >= 2) setCoasterScreen(currentCoaster-1);
  else if (currentCoaster == 1) setScreen('getThereEarlyScreen');
}

function infoScr(screen){
  setScreen('sixFlagsInfo');
  statusInfo = screen;
}

function leaveInfoScr(){
  setScreen(statusInfo);
  statusInfo = undefined;
}

onEvent('backButton', 'click', previousCoaster);
onEvent('nextButton', 'click', nextCoaster);
onEvent('infoButton', 'click', function(){
  infoScr('templateScreen');
});
onEvent('backBtnInfoScr', 'click', leaveInfoScr);
onEvent('homeButton', 'click', function(){
  setScreen('homeScreen');
});


onEvent('homeButtonWIRDScr', 'click', function(){
  setScreen('homeScreen');
});
onEvent('homeBtnGTEScr', 'click', function(){
  setScreen('homeScreen');
});

onEvent('homeButtonRDScr', 'click', function(){
  statusInfo = '';
  setScreen('homeScreen');
});
onEvent('nextButtonHomeScr', 'click', function( ) {
  setScreen('whatIsRopeDropScreen');
});
onEvent('nextButtonWIRDScr', 'click', function( ) {
  setScreen('getThereEarlyScreen');
});
onEvent('nextButtonGTEScr', 'click', function( ) {
  setScreen('templateScreen');
  setCoasterScreen(1);
});

onEvent('infoBtnHomeScr', 'click', function(){
	infoScr('homeScreen');
});
onEvent('infoBtnGetThereEarlyScr', 'click', function(){
	infoScr('getThereEarlyScreen');
});

onEvent('infoBtnRopeDropScr', 'click', function(){
  infoScr('ropeDropScreen');
});

onEvent('infoBtnWhatIsRopeDropScr', 'click', function(){
	infoScr('whatIsRopeDropScreen');
});

onEvent('facebookBtn', 'click', function(){
  open('https://facebook.com/SFGreatAmerica');
});
onEvent('instagramBtn', 'click', function(){
	open('https://instagram.com/sfgreat_america');
});
onEvent('xBtn', 'click', function(){
	open('https://x.com/sfgreatamerica');
});
onEvent('youtubeBtn', 'click', function(){
	open('https://youtube.com/@sixflagsgreatamerica');
});
onEvent('websiteBtn', 'click', function(){
	open('https://www.sixflags.com/greatamerica');
});

onEvent('homeButtonWIRDScr', 'click', function(){
	setScreen('homeScreen');
});
onEvent('backBtnRDScr', 'click', function(){
	setScreen('templateScreen');
});

onEvent('previousButtonGTEScr', 'click', function(){
	setScreen('whatIsRopeDropScreen');
});

/*
 * The following code is the minimized, cleaner formatting.
 * It is in this comment block because App Lab throws an
 * error when showing it as blocks.
 
 * Start Code
 
// ==============================================================
// =====================HOME BUTTONS=============================
// ==============================================================
var statusInfo = '';
var currentCoaster = 0;

var coasterInfo = [
  {
    'Maxx Force':{
    'id': 1,
    'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/348s.jpg',
    'message': 'The ride won\'t open immediately. If you see more than 20 people, go to the next ride.'
  }
  },
  {
    'Sky Striker': {
    'id': 2,
    'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/images.jpeg',
    'message': 'You do NOT want to wait more than 40 minutes for this ride.'
  }
    },
  {
  'Goliath': {
    'id': 3,
    'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/rdpyv92t5q4f1.jpeg',
    'message': 'This line moves VERY slow; get on it early.'
  }
  },
  {
    'Raging Bull': {
    'id': 4,
    'image': 'https://studio.code.org/v3/assets/7893ff3f-4337-4000-a716-9ce101c903f6/images-2.jpeg',
    'message': 'This line should fill up mid-day, but it moves fast.'
  }
  }];

function setCoasterScreen(id){
  id = (typeof id !== 'undefined') ? id : 1;
  var singleCoasterInfo = {};
  
  for (var i = 0; i < coasterInfo.length; i++) {
    var coasterName = Object.keys(coasterInfo[i])[0];
    if (coasterInfo[i][coasterName].id === id) {
      singleCoasterInfo = coasterInfo[i][coasterName];
      singleCoasterInfo.name = coasterName;
      break;
    }
  }
  currentCoaster = singleCoasterInfo ? id : 0;
  setProperty('rideName', 'text', singleCoasterInfo.name);
  setProperty('rideImage', 'image', singleCoasterInfo.image);
  setProperty('rideMessage', 'text', singleCoasterInfo.message);
  playSound("assets/category_bell/notification_4.mp3");5
}

function nextCoaster(){
  if (currentCoaster <= 3 && currentCoaster >= 1) setCoasterScreen(currentCoaster+1);
  else if (currentCoaster == 4) setScreen('ropeDropScreen');
}

function previousCoaster(){
  if (currentCoaster <= 4 && currentCoaster >= 2) setCoasterScreen(currentCoaster-1);
  else if (currentCoaster == 1) setScreen('getThereEarlyScreen');
}

function infoScr(screen){
  setScreen('sixFlagsInfo');
  statusInfo = screen;
}

function leaveInfoScr(){
  setScreen(statusInfo);
  statusInfo = undefined;
}

onEvent('backButton', 'click', previousCoaster);
onEvent('nextButton', 'click', nextCoaster);
onEvent('infoButton', 'click', function(){  infoScr('templateScreen') });
onEvent('backBtnInfoScr', 'click', leaveInfoScr);
onEvent('homeButton', 'click', function(){  setScreen('homeScreen') });
onEvent('homeButtonWIRDScr', 'click', function(){ setScreen('homeScreen') });
onEvent('homeBtnGTEScr', 'click', function(){ setScreen('homeScreen') });
onEvent('homeButtonRDScr', 'click', function(){
  statusInfo = '';
  setScreen('homeScreen');
});
onEvent('nextButtonHomeScr', 'click', function(){ setScreen('whatIsRopeDropScreen') });
onEvent('nextButtonWIRDScr', 'click', function(){  setScreen('getThereEarlyScreen')  });
onEvent('nextButtonGTEScr', 'click', function(){
  setScreen('templateScreen');
  setCoasterScreen(1);
});

onEvent('infoBtnHomeScr', 'click', function(){  infoScr('homeScreen') });
onEvent('infoBtnGetThereEarlyScr', 'click', function(){ infoScr('getThereEarlyScreen')  });
onEvent('infoBtnRopeDropScr', 'click', function(){  infoScr('ropeDropScreen') });
onEvent('infoBtnWhatIsRopeDropScr', 'click', function(){  infoScr('whatIsRopeDropScreen') });
onEvent('facebookBtn', 'click', function(){ open('https://facebook.com/SFGreatAmerica') });
onEvent('instagramBtn', 'click', function(){  open('https://instagram.com/sfgreat_america') });
onEvent('xBtn', 'click', function(){  open('https://x.com/sfgreatamerica')  });
onEvent('youtubeBtn', 'click', function(){  open('https://youtube.com/@sixflagsgreatamerica') });
onEvent('websiteBtn', 'click', function(){  open('https://www.sixflags.com/greatamerica')  });
onEvent('homeButtonWIRDScr', 'click', function(){ setScreen('homeScreen') });
onEvent('backBtnRDScr', 'click', function(){  setScreen('templateScreen') });
onEvent('previousButtonGTEScr', 'click', function(){  setScreen('whatIsRopeDropScreen') });

 * End Code
*/
```