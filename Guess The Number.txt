% GAME_NAME:(GUESS THE NUMBER!!!);CREATOR:(MOBIN_GHAVIDEL)
% Version(0.0.2)
% Hope_you_enjoy_it!
% Set Variables
selectedOption = 0;
score_level_1 = 0;
score_level_2 = 0;
score_level_3 = 0;
score_level_4 = 0;
score_level_5 = 0;
score_level_6 = 0;
player_boss = 0;
guess_limit = 5;
game_over = 0;
player1 = 0;
question_limit = 0;
% Game Starts
clc
% musics
music = menu ('play music?(more songs will be added in new versions!)','bethoven moonlight sonata','Nothing');
if music == 1
disp('loading the song it can take quite a while. please be patient...')
filePath = 'C:\Users\Homelan\Desktop\Beethoven_Moonlight_Sonata_Full_4591dCHe_sE_140.mp3';
[audio, sampleRate] = audioread(filePath);
% Create an audioplayer object
player1 = audioplayer(audio, sampleRate);
% Play the audio
play(player1);
clc
end
% Introduction
Name = {};
Player_Name = input('What is your name? ', 's');
i = 1;
Name {i} = Player_Name;
disp('___________________________________________________________________________');
disp(['Hello ', Player_Name, ' and welcome to Matlab games (GUESS THE NUMBER!!!)']);
pause(3);
disp('___________________________________________________________________________');
disp(['I am Mr. Math, but you can call me Mr. M for short, ', Player_Name, '.']);
pause(3);
disp('___________________________________________________________________________');
disp('The creator of me and this game is Mobin so... shout out to Mobin!');
pause(3);
disp('___________________________________________________________________________');
disp('In this game, based on your difficulty, you have to guess the number I choose.');
pause(4);
disp('___________________________________________________________________________');
disp('You can ask me questions, just wait 3 seconds and I will give you the honest answer. I promise!');
pause(4);
disp('___________________________________________________________________________');
disp('But here is the catch: you have a limited number of questions to ask, so be careful.');
pause(5);
disp('___________________________________________________________________________');
disp('For the first 2 level you have to guess the number after you asked your question ');
pause(5);
disp('___________________________________________________________________________');
disp('Don''t worry if you guess the number sooner than the guess limit i will add the remainings to your next question limit so it will not be wasted.');
pause(8);
disp('___________________________________________________________________________');
% Explaining Questions
disp('Here are the questions you can ask:')
pause(2)
disp('___________________________________________________________________________');
disp('Type 1 for: is this number a multiple of x(i)?')
pause(1)
disp('___________________________________________________________________________');
disp('Type 2 for: is this number odd or even?')
pause(1)
disp('___________________________________________________________________________');
disp('Type 3 for: is this number primal?')
pause(1)
disp('___________________________________________________________________________');
disp('Type 4 for: how many digits does it have?')
pause(1)
disp('___________________________________________________________________________');
disp('Type 5 for: Is Secret number higher or lower than number x(i)?')
pause(1)
disp('___________________________________________________________________________');
disp('Type 6 for: Is Secret number irreversible?')
pause(1)
disp('___________________________________________________________________________');
% Explaining Difficulties
disp('We have 5 difficulties:')
pause(1)
disp('___________________________________________________________________________');
disp('1-Baby')
pause(0.75)
disp('___________________________________________________________________________');
disp('2-Easy')
pause(0.75)
disp('___________________________________________________________________________');
disp('3-Medium')
pause(0.75)
disp('___________________________________________________________________________');
disp('4-Hard')
pause(0.75)
disp('___________________________________________________________________________');
disp('5-Master')
pause(0.75)
disp('___________________________________________________________________________');
disp('6-***** ******')
pause(1);
disp('_____________________________________________________________________________________________');
disp('In baby mode, I choose a number between 1:10 and you have 5 guesses! It''s great! Isn''t it?')
pause(10);
disp('_____________________________________________________________________________________________');
disp('In easy mode, I choose a number between 1:30 and you have 5 guesses! Just a little warm-up!')
pause(10);
disp('_____________________________________________________________________________________________');
disp('In medium mode, I choose a number between 1:50 and you have 5 guesses and 5 + (guess remainings) questions to ask!')
pause(10);
disp('_____________________________________________________________________________________________');
disp('In hard mode, I choose a number between 1:80 and you have 5 guesses and 5 + (guess remainings) questions to ask.though guy!')
pause(10);
disp('_____________________________________________________________________________________________');
disp('In master mode, I choose a number between 1:111 and you have 5 + (guess remainings) questions to ask! Can you do it?')
pause(10);
disp('_____________________________________________________________________________________________');
disp('I don''t want to talk about the ***** ****** mode; it is a secret and only the ones that surpass the master mode will reach this Math_sacred entity')
pause(10);
disp('_____________________________________________________________________________________________');
disp('Let''s cut to the chase and begin the game')
pause(5);
disp('_____________________________________________________________________________________________');
while true
if i > 1
   Name = {};
Player_Name = input('What is your name? ', 's');
Name {i} = Player_Name;
end
% Starting The Game
% Timer Set
tic
% Level_1
disp('Level one')
pause(2)
disp('_____________________________________________________________________________________________');
Secret_number = randi([1, 10]);
originalNumbers = 1:10;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
disp('_____________________________________________________________________________________________');
guess_limit = 5;
game_over = 0;
level = 1;
while game_over < guess_limit && level == 1
    while ask == 1 && game_over < guess_limit
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && level == 1
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && level == 1
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};        
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};  
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end

    if guess_limit == 0
        disp(['the secret number was ', num2str(Secret_number)])
        pause(5)
        disp('_____________________________________________________________________________________________');
        disp('well...you have reached the maximum guess limit, which means you couldn''t even beat baby mode')
        pause(5)
        disp('_____________________________________________________________________________________________');
        disp('the only thing I can say to you to understand it is: GOO GOO GA GA ')
        pause(5)
        disp('_____________________________________________________________________________________________');
        disp('GAME OVER')
        disp('_____________________________________________________________________________________________');
        Score_Stage = -1;
        score_level_1(i) = 0;
        score_level_2(i) = 0;
        score_level_3(i) = 0;
        score_level_4(i) = 0;
        score_level_5(i) = 0;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 0;
        time_score(i) = 0;
        break
    end
end  

%Score_level_1
if level == 2
    score_level_1(i) = guess_limit;
end

%level_2
qquestion_limit = 5;
guess_limit = 5;
while level == 2 && guess_limit ~= 0
pause(1)
disp('I didnt mean to offend you by setting a baby mode for you.i just wanted to make sure that no baby is messing with their parents PC')
pause(8)
disp('_____________________________________________________________________________________________');
disp('level two')
pause(1)
disp('_____________________________________________________________________________________________');
Secret_number = randi([1, 30]);
originalNumbers = 1:30;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
disp('_____________________________________________________________________________________________');
game_over = 0;
while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('_____________________________________________________________________________________________');
end
while game_over < guess_limit && level == 2    
    while ask == 1 && game_over < guess_limit
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && level == 2
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && level == 2
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};        
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
               ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};  
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end    
    while ask == 4 && game_over < guess_limit && level == 2
        disp('how many digits does it have?');
        pause(3)
        disp('_____________________________________________________________________________________________');
    disp(['It has ', num2str(length(num2str(Secret_number))), ' digits']);
    if length(num2str(Secret_number)) == 1
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 1, cellArray));
    elseif length(num2str(Secret_number)) == 2
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 2, cellArray));    
    end
    disp('_____________________________________________________________________________________________');
     guess = menu('Guess your number', cellArray{:});
     selectedOption = cellArray{guess};
     disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                question_limit = question_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses reamining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('_____________________________________________________________________________________________');
                    end
                end
            end
    end
end
end

%Score_level_2
if level == 3
    score_level_2(i) = guess_limit .* 5;
end

%losing_in_level_2
while guess_limit == 0 && level == 2
        disp(['the secret number was ', num2str(Secret_number)])
        pause(3)
        disp('_____________________________________________________________________________________________');
        disp('well...you lose on easy mode')
        pause(3)
        disp('_____________________________________________________________________________________________');
        disp('Come back when you passed 5th grade')
        pause(4)
        disp('_____________________________________________________________________________________________');
        disp('GAME OVER')
        disp('_____________________________________________________________________________________________');
        Score_Stage = -1;
        score_level_2(i) = 0;
        score_level_3(i) = 0;
        score_level_4(i) = 0;
        score_level_5(i) = 0;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 1;
        time_score(i) = 0;
        break
end

%level_3
question_limit = 5 + guess_limit;
guess_limit = 5;
while level == 3 && guess_limit ~= 0
pause(1)
disp('Certainly you are smarter than a 5th grader now you are going to be tested in medium mode')
pause(5)
disp('___________________________________________________________________________');
disp('level three')
pause(1.5)
disp('___________________________________________________________________________');
Secret_number = randi([1, 50]);
originalNumbers = 1:50;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
disp('___________________________________________________________________________');
game_over = 0;
while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = input('ask your question(1, 2, 3 or 4): ');
    disp('___________________________________________________________________________');
end
while game_over < guess_limit && level == 3
    while ask == 1 && game_over < guess_limit && question_limit > 0 && level == 3
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            disp('_____________________________________________________________________________________________');
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});          
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && question_limit > 0 && level == 3
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));  
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && question_limit > 0 && level == 3
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end       
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end    
    while ask == 4 && game_over < guess_limit && question_limit > 0 && level == 3
        disp('how many digits does it have?');
        pause(3)
        disp('_____________________________________________________________________________________________');
    disp(['It has ', num2str(length(num2str(Secret_number))), ' digits']);
    if length(num2str(Secret_number)) == 1
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 1, cellArray));
    elseif length(num2str(Secret_number)) == 2
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 2, cellArray));    
    end
    disp('_____________________________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('___________________________________________________________________________');
            end
            break
            end
     disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                question_limit = question_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses reamining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
                    disp('_____________________________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?');
    disp('_____________________________________________________________________________________________');
                    end
                end
            end
    end
    if question_limit == 0
    disp(['OK you have reached your maximum question limit. now guess the number ' ,Player_Name, ' .']);
    disp('___________________________________________________________________________');
    end
    while question_limit == 0 && game_over < guess_limit
        guess = menu('Guess your number', cellArray{:});
        selectedOption = cellArray{guess};
        disp('___________________________________________________________________________');
        if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                end
        end
    end
end
end

%Score_level_3
if level == 4
    score_level_3(i) = guess_limit .* 10 + question_limit .* 20;
end

%losing_in_level_3
while guess_limit == 0 && level == 3
        disp(['the secret number was ', num2str(Secret_number)])
        pause(3)
        disp('___________________________________________________________________________');
        disp('well...you lost on Medium mode')
        pause(3)
        disp('___________________________________________________________________________');
        disp('But I believe in you come back when you are ready to go')
        pause(4)
        disp('___________________________________________________________________________');
        disp('GAME OVER')
        disp('___________________________________________________________________________');
        Score_Stage = -1;
        score_level_3(i) = 0;
        score_level_4(i) = 0;
        score_level_5(i) = 0;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 31;
        time_score(i) = 0;
        break
end

%level_4
question_limit = question_limit + guess_limit + 5;
guess_limit = 5;
while level == 4 && guess_limit ~= 0
pause(1)
disp('Looks like we got a smart human being here right?from this level things will get a little hard.GOOD LUCK')
pause(5)
disp('___________________________________________________________________________');
disp('Level Four')
pause(1.5)
disp('___________________________________________________________________________');
Secret_number = randi([1,80]);
originalNumbers = 1:80;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
disp('___________________________________________________________________________');
game_over = 0;
while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && level == 4
    disp('sorry you can use only Q1 , Q2, Q3, Q4 or Q5 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
end
while game_over < guess_limit && level == 4
    while ask == 1 && game_over < guess_limit && question_limit > 0 && level == 4
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            disp('_____________________________________________________________________________________________');
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});          
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && question_limit > 0 && level == 4
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));  
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && question_limit > 0 && level == 4
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end       
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end    
    while ask == 4 && game_over < guess_limit && question_limit > 0 && level == 4
        disp('how many digits does it have?');
        pause(3)
        disp('_____________________________________________________________________________________________');
    disp(['It has ', num2str(length(num2str(Secret_number))), ' digits']);
    if length(num2str(Secret_number)) == 1
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 1, cellArray));
    elseif length(num2str(Secret_number)) == 2
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 2, cellArray));    
    end
    disp('_____________________________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
     disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                question_limit = question_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses reamining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('_____________________________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('_____________________________________________________________________________________________');
                    end
                end
            end
    end
    while ask == 5 && game_over < guess_limit && question_limit > 0 && level == 4
        compare_number = input('Is Secret number higher or lower than number?');
        pause(3)
        disp('___________________________________________________________________________');
   if compare_number >= Secret_number
        disp('your number is higher than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) > compare_number, cellArray);
        cellArray(indicesToRemove) = [];
    elseif compare_number <= Secret_number
        disp('your number is lower than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) < compare_number, cellArray);
        cellArray(indicesToRemove) = [];
   end
    disp('___________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && level == 4
    disp('sorry you can use only Q1 , Q2, Q3, Q4 or Q5 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
                     end
                end
            end
    end
    if question_limit == 0
    disp(['OK you have reached your maximum question limit. now guess the number ' ,Player_Name, ' .']);
    disp('___________________________________________________________________________');
    end
    while question_limit == 0 && game_over < guess_limit
        guess = menu('Guess your number', cellArray{:});
        selectedOption = cellArray{guess};
        disp('___________________________________________________________________________');
        if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                end
        end
    end
end
end

%Score_level_4
if level == 5
    score_level_4(i) = guess_limit .* 14 + question_limit .* 40;
end

%losing_in_level_4
while guess_limit == 0 && level == 4
        disp(['the secret number was ', num2str(Secret_number)])
        pause(3)
        disp('___________________________________________________________________________');
        disp('well...you lost on hard mode.you did well...honestly')
        pause(3)
        disp('___________________________________________________________________________');
        disp('I would like to call as a human who is closely smart but not quite')
        pause(4)
        disp('___________________________________________________________________________');
        disp('GAME OVER')
        disp('___________________________________________________________________________');
        Score_Stage = -1;
        score_level_4(i) = 0;
        score_level_5(i) = 0;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 81;
        time_score(i) = 0;
        break
end

%level_5
question_limit = question_limit + guess_limit + 5;
guess_limit = 5;
irreversible_num_lvl_5 = num2cell([1,2,3,4,5,6,7,8,9,11,22,33,44,55,66,77,88,99,111]);
while level == 5 && guess_limit ~= 0
pause(1)
disp('HA HA!I liked it!you are actully an smart person!Glad to find such a human being but you better be ready for this one.things are getting serious.can you be a Master?')
pause(7)
disp('___________________________________________________________________________');
disp('Level Five')
pause(1.5)
disp('___________________________________________________________________________');
Secret_number = randi([1, 111]);
originalNumbers = 1:111;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
disp('___________________________________________________________________________');
game_over = 0;
while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && ask ~= 6 && level == 5
    disp('sorry you can use only Q1 , Q2, Q3, Q4, Q5 or Q6 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
end
while game_over < guess_limit && level == 5
    while ask == 1 && game_over < guess_limit && question_limit > 0 && level == 5
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            disp('_____________________________________________________________________________________________');
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});          
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?','Is Secret number higher or lower than number?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && question_limit > 0 && level == 5
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));  
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && question_limit > 0 && level == 5
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end       
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end    
    while ask == 4 && game_over < guess_limit && question_limit > 0 && level == 5
        disp('how many digits does it have?');
        pause(3)
        disp('_____________________________________________________________________________________________');
    disp(['It has ', num2str(length(num2str(Secret_number))), ' digits']);
    if length(num2str(Secret_number)) == 1
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 1, cellArray));
    elseif length(num2str(Secret_number)) == 2
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 2, cellArray));    
    elseif length(num2str(Secret_number)) == 3
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 3, cellArray));    
    end
    disp('_____________________________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
     disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                question_limit = question_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses reamining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('_____________________________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('_____________________________________________________________________________________________');
                    end
                end
            end
    end
    while ask == 5 && game_over < guess_limit && question_limit > 0 && level == 5
        compare_number = input('Is Secret number higher or lower than number?');
        pause(3)
        disp('___________________________________________________________________________');
   if compare_number >= Secret_number
        disp('your number is higher than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) > compare_number, cellArray);
        cellArray(indicesToRemove) = [];
    elseif compare_number <= Secret_number
        disp('your number is lower than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) < compare_number, cellArray);
        cellArray(indicesToRemove) = [];
   end
    disp('___________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && level == 4
    disp('sorry you can use only Q1 , Q2, Q3, Q4 or Q5 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
                     end
                end
            end
    end
    while ask == 6 && game_over < guess_limit && question_limit > 0 && level == 5
        disp('Is this number irreversible?');
        pause(3)
        disp('___________________________________________________________________________');
        string_number = num2str(Secret_number);
        reverse_number = fliplr(string_number);
    if str2double(string_number) == str2double(reverse_number)
        disp('your number is irreversible')
        indicesToKeep = ismember(cellArray, cellfun(@num2str, irreversible_num_lvl_5, 'UniformOutput', false));
        cellArray = cellArray(indicesToKeep);
    else
        disp('your number is not irreversible')
        cellArray = cellfun(@num2str, cellArray, 'UniformOutput', false);
indicesToRemove = ismember(cellArray, cellfun(@num2str, irreversible_num_lvl_5, 'UniformOutput', false));
cellArray(indicesToRemove) = [];
    end
    disp('___________________________________________________________________________');
      guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && ask ~= 6 && level == 5
    disp('sorry you can use only Q1 , Q2, Q3, Q4, Q5 or Q6 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?');
    disp('___________________________________________________________________________');
                     end
                end
            end
   end

    if question_limit == 0
    disp(['OK you have reached your maximum question limit. now guess the number ' ,Player_Name, ' .']);
    disp('___________________________________________________________________________');
    end
    while question_limit == 0 && game_over < guess_limit
        guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
        disp('___________________________________________________________________________');
        if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses'])
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                end
        end
    end
end
end

%Score_level_5
if level == 6
    score_level_5(i) = guess_limit .* 17 + question_limit .* 60;
end

%losing_in_level_5
while guess_limit == 0 && level == 5
        disp(['the secret number was ', num2str(Secret_number)])
        pause(3)
        disp('___________________________________________________________________________');
        disp('OH NO!You lost in master mode!such a pity.')
        pause(3)
        disp('___________________________________________________________________________');
        disp('to be honest.I like you because you are smart but...I dont respect you because you are not as smart as me.you are much far away to reach my wisdom')
        pause(6)
        disp('___________________________________________________________________________');
        disp('GAME OVER')
        disp('___________________________________________________________________________');
        Score_Stage = -1;
        score_level_5(i) = 0;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 161;
        time_score(i) = 0;
        break
end

%level_6
question_limit = 10;
guess_limit = 1;
irreversible_num_lvl_5 = num2cell([1,2,3,4,5,6,7,8,9,11,22,33,44,55,66,77,88,99,111,222,333,444,555,666]);
irreversible_num_lvl_5_char = cellfun(@num2str, irreversible_num_lvl_5, 'UniformOutput', false);
while level == 6 && guess_limit ~= 0
disp('OMG,I can not believe it that you actually beat the master mode!!!you are offically Master.')
pause(7)
disp('___________________________________________________________________________');
disp('You can get your prize from Mobin now!!!');
pause(4);
dialogue = menu('choose your dialogue','1-OK,Thank you Mr.Math','2-But i wanna know about ***** ****** mode you talked about!');
disp('___________________________________________________________________________');
if dialogue == 1
    disp('You Win')
    disp('___________________________________________________________________________');
    score_level_6(i) = 0;
    Score_Stage = 0;
    time_elapsed(i) = toc; 
    if time_elapsed(i) <= 1620
        time_score(i) = 600 + (1620 - time_elapsed(i)) * 3;
    elseif 1620 < time_elapsed(i) && time_elapsed(i) <= 3240
        time_score(i) = 450 + (3240 - time_elapsed(i)) * 2;
    elseif 3240 < time_elapsed(i) && time_elapsed(i) <= 4860
        time_score(i) = 300 + (4860 - time_elapsed(i)) * 1;
    elseif 4860 < time_elapsed(i)
        time_score(i) = 200;
    end
    disp('levels beaten = 5 ====================================> 1 + 30 + 50 + 80 + 100 = 261 Points')
    pause(2)
    disp(['questions and guesses remaining from levels ==========> ', num2str(score_level_1(i)), ' + ', num2str(score_level_2(i)), ' + ', num2str(score_level_3(i)), ' + ', num2str(score_level_4(i)), ' + ', num2str(score_level_5(i)),' = ', num2str(score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i)),' Ponits']);
    pause(2)
    disp(['time elapsed = time_elapsed ==========================> ',num2str(time_score(i)),' Points'])
    pause(2)
    disp(['total score ==========================================> ',num2str(time_score(i) + score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i) + 261),' Points'])
    pause(2)
    disp('*******************************************************************************');
    level = 0;
    break
end
    if dialogue == 2
    disp(['Look ', Player_Name, ', I get it. You are as smart as me, and I respect it. But it doesn''t have to do anything with playing in ***** ******. Are you sure you want to play it?']);
    pause(10)
    dialogue_2 = menu('choose your dialogue','1-Yes I want to','2-Actually Never mind');
    if dialogue_2 == 2
        disp('___________________________________________________________________________');
    disp(['Wise Choice ', Player_Name, '.']);
    disp('___________________________________________________________________________');
    pause(2)
    disp('___________________________________________________________________________');
    disp('You Win')
    disp('___________________________________________________________________________');
    score_level_6(i) = 0;
    Score_Stage = 0;
    time_elapsed(i) = toc; 
    if time_elapsed(i) <= 1620
        time_score(i) = 600 + (1620 - time_elapsed(i)) * 3;
    elseif 1620 < time_elapsed(i) && time_elapsed(i) <= 3240
        time_score(i) = 450 + (3240 - time_elapsed(i)) * 2;
    elseif 3240 < time_elapsed(i) && time_elapsed(i) <= 4860
        time_score(i) = 300 + (4860 - time_elapsed(i)) * 1;
    elseif 4860 < time_elapsed(i)
        time_score(i) = 200;
    end
    disp('levels beaten = 5 ====================================> 1 + 30 + 50 + 80 + 100 = 261 Points')
    pause(1)
    disp(['questions and guesses remaining from levels ==========> ', num2str(score_level_1(i)), ' + ', num2str(score_level_2(i)),...
        ' + ', num2str(score_level_3(i)), ' + ', num2str(score_level_4(i)), ' + ', num2str(score_level_5(i)),...
        ' = ', num2str(score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i)),' Ponits']);
    pause(1)
    disp(['time elapsed = time_elapsed ==========================> ',num2str(time_score(i)),' Points'])
    pause(1)
    disp(['total score ==========================================> ',num2str(time_score(i) + score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i) + 261),' Points'])
    pause(1)
    disp('*******************************************************************************');
    level = 0;
    break
    end
    if dialogue_2 == 1
        disp('___________________________________________________________________________');
        disp(['OK ', Player_Name, ' the ***** ****** mode is called [GRAND MASTER] mode'])
        pause(10)
        disp('___________________________________________________________________________');
        disp('Even me couldnt beat this mode that''s why i censor it for players')
        pause(10)
        disp('___________________________________________________________________________');
        disp('With 10 question and only 1 guess you have to guess the number between 1:666 can you do it? I dont think so.')
        pause(10)
        disp('___________________________________________________________________________');
        disp('Also i can give you the ultimate weapon for this mode:(Q7)')
        pause(10)
        disp('___________________________________________________________________________');
        disp('Q7=is this number between x and y?')
        pause(2)
        disp('___________________________________________________________________________');
        disp('GOOD LUCK')
        pause(1)
        disp('___________________________________________________________________________');
    end
    end  
    if music == 1
    stop(player1)
    end
    disp('loading the song it can take quite a while. please be patient...')
filePath2 = 'C:\Users\Homelan\Desktop\Chopin_Etude_Op._25_No._11_Winter_Wind_gZjdAWgjLx8_140.mp3';
[audio, sampleRate] = audioread(filePath2);
% Create an audioplayer object
player_boss = audioplayer(audio, sampleRate);
% Play the audio
play(player_boss);
Secret_number = randi([1, 666]);
originalNumbers = 1:666;
cellArray = arrayfun(@num2str, originalNumbers, 'UniformOutput', false);
ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
disp('___________________________________________________________________________');
game_over = 0;
while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && ask ~= 6 && ask ~= 7 && level == 6
    disp('sorry you can use only Q1 , Q2, Q3, Q4, Q5, Q6 or Q7 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
end
while game_over < guess_limit && level == 6
    while ask == 1 && game_over < guess_limit && question_limit > 0 && level == 6
        multiple_number = input('Is this number a multiple of? ');
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, multiple_number) == 0
            disp('YES it is')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) == 0, cellArray));
            disp('_____________________________________________________________________________________________');
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});          
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('NO it is not')
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), multiple_number) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
           ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 2 && game_over < guess_limit && question_limit > 0 && level == 6
        disp('Is this number odd or even?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if rem(Secret_number, 2) == 0
            disp('It is EVEN')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) == 0, cellArray));  
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, It is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is ODD')
            disp('_____________________________________________________________________________________________');
            cellArray = cellArray(cellfun(@(x) mod(str2double(x), 2) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end
    while ask == 3 && game_over < guess_limit && question_limit > 0 && level == 6
        disp('is this number prime?')
        pause(3)
        disp('_____________________________________________________________________________________________');
        if isprime(Secret_number) == 1
            disp('it is prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) ~= 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end       
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        else
            disp('it is not prime')
            cellArray = cellArray(cellfun(@(x) isprime(str2double(x)) == 0, cellArray));
            guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!')
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses remaining.'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
               ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                end
            end
        end
    end    
    while ask == 4 && game_over < guess_limit && question_limit > 0 && level == 6
        disp('how many digits does it have?');
        pause(3)
        disp('_____________________________________________________________________________________________');
    disp(['It has ', num2str(length(num2str(Secret_number))), ' digits']);
    if length(num2str(Secret_number)) == 1
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 1, cellArray));
    elseif length(num2str(Secret_number)) == 2
    cellArray = cellArray(cellfun(@(x) length(num2str(x)) == 2, cellArray));    
    end
    disp('_____________________________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Guess your number', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
     disp('_____________________________________________________________________________________________');
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('_____________________________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                question_limit = question_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses reamining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('_____________________________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('_____________________________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 2
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    disp('_____________________________________________________________________________________________');
    pause(0.5)
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('_____________________________________________________________________________________________');
                    end
                end
            end
    end
    while ask == 5 && game_over < guess_limit && question_limit > 0 && level == 6
        compare_number = input('Is Secret number higher or lower than number?');
        pause(3)
        disp('___________________________________________________________________________');
   if compare_number >= Secret_number
        disp('your number is higher than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) > compare_number, cellArray);
        cellArray(indicesToRemove) = [];
    elseif compare_number <= Secret_number
        disp('your number is lower than Secret number')
        indicesToRemove = cellfun(@(x) str2double(x) < compare_number, cellArray);
        cellArray(indicesToRemove) = [];
   end
    disp('___________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                cellArray = cellArray(~strcmp(cellArray, selectedOption));
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && level == 4
    disp('sorry you can use only Q1 , Q2, Q3, Q4 or Q5 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
                     end
                end
            end
    end
    while ask == 6 && game_over < guess_limit && question_limit > 0 && level == 6
        disp('Is this number irreversible?');
        pause(3)
        disp('___________________________________________________________________________');
        string_number = num2str(Secret_number);
        reverse_number = fliplr(string_number);
    if str2double(string_number) == str2double(reverse_number)
        disp('your number is irreversible')
        indicesToKeep = ismember(cellArray, cellfun(@num2str, irreversible_num_lvl_5, 'UniformOutput', false));
        cellArray = cellArray(indicesToKeep);
    else
        disp('your number is not irreversible')
        cellArrayChar = cellfun(@num2str, cellArray, 'UniformOutput', false);
indicesToRemove = ismember(cellArrayChar, cellfun(@num2str, irreversible_num_lvl_5, 'UniformOutput', false));
cellArray(indicesToRemove) = [];
    end
    disp('___________________________________________________________________________');
      guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray);
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
   ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('Nice one!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && ask ~= 6 && level == 5
    disp('sorry you can use only Q1 , Q2, Q3, Q4, Q5 or Q6 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
                     end
                end
            end
    end
    while ask == 7 && game_over < guess_limit && question_limit > 0 && level == 6
        disp('Is this number between x and y?');
        pause(3)
        disp('___________________________________________________________________________');
        starting_number = input('what is you starting number? ');
        ending_number = input('what is you ending number? ');
        disp('___________________________________________________________________________');
    if (starting_number < Secret_number) && (Secret_number < ending_number) == 1
        pause(3)
        disp('your number is in the range')
        indicesToKeep = cellfun(@(x) str2double(x) >= starting_number && str2double(x) <= ending_number, cellArray);
cellArray = cellArray(indicesToKeep);
        disp('___________________________________________________________________________');
    else
        pause(3)
        disp('your number is not in the range')
        indicesToKeep = cellfun(@(x) str2double(x) <= starting_number || str2double(x) >= ending_number, cellArray);
cellArray = cellArray(indicesToKeep);
        disp('___________________________________________________________________________');
    end
    disp('___________________________________________________________________________');
     guess_tendency = menu('Do you wanna guess the number?','yes','no');
            if guess_tendency == 1
            guess = menu('Choose a number:', cellArray{:});
            selectedOption = cellArray{guess};
            disp('___________________________________________________________________________');
            question_limit = question_limit - 1;
            else
                question_limit = question_limit - 1;
                disp(['You have ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
            ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
            disp('___________________________________________________________________________');
            while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && level == 3
    disp('sorry you can use only Q1 , Q2, Q3 or Q4 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
            end
            break
            end
            if str2double(selectedOption) == Secret_number
                disp('You...YOU DID IT!!!');
                disp('___________________________________________________________________________');
                level = level + 1;
                break
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses and ' , num2str(question_limit), ' questions remaining'])
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
                    disp('___________________________________________________________________________');
                    while ask ~= 1 && ask ~= 2 && ask ~= 3 && ask ~= 4 && ask ~= 5 && ask ~= 6 && ask ~= 7 && level == 6
    disp('sorry you can use only Q1 , Q2, Q3, Q4, Q5, Q6 or Q7 in this mode')
    pause(0.5)
    disp('___________________________________________________________________________');
    ask = menu ('Ask your question' , 'Is this number a multiple of?','Is this number odd or even?','Is this number prime?','How many digits does it have?',...
'Is Secret number higher or lower than number?','Is this number irreversible?','Is this number between x and y?');
    disp('___________________________________________________________________________');
                    end
                end
            end
   end

    if question_limit == 0
    disp(['OK you have reached your maximum question limit. now guess the number ' ,Player_Name, ' .']);
    disp('___________________________________________________________________________');
    end
    while question_limit == 0 && game_over < guess_limit
        guess = menu('Guess your number', cellArray{:});
        selectedOption = cellArray{guess};
        disp('___________________________________________________________________________');
        if str2double(selectedOption) == Secret_number
                disp('You...YOU DID IT!!!');
                disp('___________________________________________________________________________');
                level = level + 1;
            else
                guess_limit = guess_limit - 1;
                disp(['NO, it is wrong. Try again. You have ', num2str(guess_limit), ' guesses'])
                disp('___________________________________________________________________________');
                if guess_limit ~= 0
                end
        end
    end
end
end

%Win_dialogue
while level == 7
    pause(1)
    disp(['HOLY COW.HOW DID YOU DO THAT ',Player_Name,'!!??JUST HOW?!'])
    pause(4)
    disp('*******************************************************************************');
    disp('FOR THE FIRST TIME EVER,SOMEONE BEATS THE MOST HELISH MODE IN THE MATH WORLD')
    pause(5)
      disp('*******************************************************************************');
    disp('IF YOU TELL THIS TO MOBIN HE WILL BE SHOCKED AS HELL')
    pause(3)
      disp('*******************************************************************************');
    disp('IF YOU SEE MOBIN TELL HIM THAT YOU BEAT {GRAND MASTER} MODE HE WILL GIVE YOU A PRIZE MORE THAN BEATING MASTER MODE')
    pause(6)
      disp('*******************************************************************************');
    disp(['I ADMIT YOU ARE SMARTER THAN ME.I AM NO LONGER MR.Math.ALLOW ME TO CALL MYSELF FROM NOW ON MR/MRS ',Player_Name,'.'])
    pause(6)
      disp('*******************************************************************************');
    disp(['ITS BEEN A PLEASURE PLAYING WITH YOU HOPE WE SEE EACH OTHER IN THE FUTURE!BUT NOW IT IS TIME TO SAY GOODBYE...FAREWELL ',Player_Name,'.'])
    pause(7)
      disp('*******************************************************************************');
    disp('YOU WIN')
    disp('*******************************************************************************');
score_level_6(i) = question_limit * 1213;
    time_elapsed(i) = toc; 
    if time_elapsed(i) <= 1620
        time_score(i) = 600 + (1620 - time_elapsed(i)) * 3;
    elseif 1620 < time_elapsed(i) && time_elapsed(i) <= 3240
        time_score(i) = 450 + (3240 - time_elapsed(i)) * 2;
    elseif 3240 < time_elapsed(i) && time_elapsed(i) <= 4860
        time_score(i) = 300 + (4860 - time_elapsed(i)) * 1;
    elseif 4860 < time_elapsed(i)
        time_score(i) = 200;
    end
    disp('levels beaten = 6 ====================================> 1 + 30 + 50 + 80 + 100 + 666 = 927 Points')
    pause(1)
    disp(['questions and guesses remaining from levels ==========> ', num2str(score_level_1(i)), ' + ', num2str(score_level_2(i)), ' + ', num2str(score_level_3(i)), ' + ', num2str(score_level_4(i)), ' + ', num2str(score_level_5(i)), ' + ', num2str(score_level_6(i)), ' = ', num2str(score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i) + score_level_6(i)),' Ponits']);
    pause(1)
    disp(['time elapsed = time_elapsed ==========================> ',num2str(time_score(i)),' Points'])
    pause(1)
    disp(['total score ==========================================> ',num2str(time_score(i) + score_level_1(i) + score_level_2(i) + score_level_3(i) + score_level_4(i) + score_level_5(i) + score_level_6(i) + 927),' Points'])
    pause(1)
    disp('*******************************************************************************');
    level = 0;
    Score_Stage = 1;
    break
end

%losing_in_level_6
while guess_limit == 0 && level == 6
        disp(['the secret number was ', num2str(Secret_number)])
        pause(3)
        disp('___________________________________________________________________________');
        disp('as I expected you lost')
        pause(3)
        disp('___________________________________________________________________________');
        disp('it''s ok.i sill respect you and your effort')
        pause(6)
        disp('___________________________________________________________________________');
        disp('dont be sad you will be happy when you get your prize from MOBIN for beating master mode ;)')
        pause(6)
        disp('___________________________________________________________________________');
        disp('YOU WIN(?)')
        disp('___________________________________________________________________________');
        Score_Stage = -1;
        score_level_6(i) = 0;
        Finishing_Game_Score(i) = 261;
        break
end
% Specify the Excel file name (modify the filename if needed)
excel_filename = 'Leaderboard.xlsx';

% Initialize a flag to check if column names have been defined
column_names_defined = false;

% Create an empty table to store the data
fullTable = table();

for i = 1:numel(Name)
    % Define column names only if not already defined
    if ~column_names_defined
        % Column names
        column_names = {'Player_Name', 'Score_Level_1', 'Score_Level_2', 'Score_Level_3', ...
                        'Score_Level_4', 'Score_Level_5', 'Score_Level_6', ...
                        'Time_Score', 'Finishing_Game_Score', 'Total_Score'};
        column_names_defined = true;  % Set the flag to true
    end
    
    % Example data
    if Score_Stage == 1
        Finishing_Game_Score(i) = 927;
    elseif Score_Stage == 0
        Finishing_Game_Score(i) = 261;
    else
        Finishing_Game_Score(i) = Finishing_Game_Score(i);
    end

for i = 1:numel(Name)
    Name{i} = {Player_Name};
end

    % Concatenate the values into a single string
    data = {Name{i}, num2str(score_level_1(i)), num2str(score_level_2(i)), num2str(score_level_3(i)), ...
            num2str(score_level_4(i)), num2str(score_level_5(i)), num2str(score_level_6(i)), ...
            num2str(time_score(i)), num2str(Finishing_Game_Score(i)), ...
            num2str(time_score(i) + score_level_1(i) + score_level_2(i) + score_level_3(i) + ...
            score_level_4(i) + score_level_5(i) + score_level_6(i) + Finishing_Game_Score(i))};
        stop(player_boss)
    % Create a table from the data
    table_data = cell2table(data, 'VariableNames', column_names);
    
    % Display or use the table as needed
    disp(table_data);

    % Append the current row to the full table
    fullTable = [fullTable; table_data];
    i = i + 1;
end

% Write the full table to an Excel file
writetable(fullTable, excel_filename);
if music == 1
    stop(player1)
end
music = menu ('play music?(more songs will be added in new versions!)','bethoven moonlight sonata','Nothing');
if music == 1
disp('loading the song it can take quite a while. please be patient...')
filePath = 'C:\Users\Homelan\Desktop\Beethoven_Moonlight_Sonata_Full_4591dCHe_sE_140.mp3';
[audio, sampleRate] = audioread(filePath);
% Create an audioplayer object
player1 = audioplayer(audio, sampleRate);
% Play the audio
play(player1);
end
end
