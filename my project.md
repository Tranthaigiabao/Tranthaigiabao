-- hi guys, there is my project which i'm working on:

#ifndef KEYBOARDLISTENER_H_INCLUDED
#define KEYBOARDLISTENER_H_INCLUDED

#include<windows.h>

class KeyboardListener
{
    public :
        static int getUserInteract();
    private:
        static const int BUTTON_DELAY = 500;
};

#endif // KEYBOARDLISTENER_H_INCLUDED

#ifndef MOUSELISTENER_H_INCLUDED
#define MOUSELISTENER_H_INCLUDED



#endif // MOUSELISTENER_H_INCLUDED

#ifndef GENERATOR_H_INCLUDED
#define GENERATOR_H_INCLUDED

#include"logic/Maze.h"

class Generator
{
    public :
        Generator();
        virtual~Generator();
        virtual void generateMaze(class Maze&)=0;
    protected:
        static const int NORTH =10;
        static const int EAST = 11;
        static const int SOUTH =12;
        static const int WEST = 13;

        int maze_width;             /*!< maze width*/
        int maze_height;            /*!< maze height*/
        int **generator_grid;       /*!< generator grid*/

        virtual void setGridValue(class Maze&, const int& , const int &,const int&)=0;
};

#endif // GENERATOR_H_INCLUDED

#ifndef GENERATORSYSTEM_H
#define GENERATORSYSTEM_H

#include "generator/PrimGenerator.h"
#include "generator/LoopyGenerator.h"
#include "generator/RecursiveGerenator.h"

class GeneratorSystem
{
    public:
        const int PRIM;
        const int LOOPY;
        const int RECURSIVE;
        GeneratorSystem();
        virtual ~GeneratorSystem();

        int getGenerator() const;
        void setGenerator(const unsigned int& );
        void generateMaze(class Maze&);
        int handleEvent(const int&);
    protected:

    private:
        PrimGenerator *prim;
        RecursiveGenerator *recursive;
        LoopyGenerator *loopy;
        unsigned int generator_index;
};

#endif // GENERATORSYSTEM_H

#ifndef LOOPYGENERATOR_H_INCLUDED
#define LOOPYGENERATOR_H_INCLUDED

#include"generator/Generator.h"
#include"generator/PrimGenerator.h"
#define RATE 3

class LoopyGenerator : public Generator{
    public:
        LoopyGenerator();
        virtual ~LoopyGenerator();
        void generateMaze(class Maze&);
    private:
        void setGridValue(class Maze& , const int&,const int&,const int&);
};


#endif // LOOPYGENERATOR_H_INCLUDED

#ifndef PRIMGENERATOR_H_INCLUDED
#define PRIMGENERATOR_H_INCLUDED

#include"generator/Generator.h"
#include<vector>

class PrimGenerator: public Generator
{
    public :
        PrimGenerator();
        virtual ~PrimGenerator();
        void generateMaze(class Maze&);
    private:
        const int INSIDE;
        const int FRONTER;
        const int OUTSIDE;
        std::vector<COORD> frontier_list;
        void setGridValue(class Maze&, const int& , const int &,const int&);
};

#endif // PRIMGENERATOR_H_INCLUDED

#ifndef RECURSIVEGERENATOR_H_INCLUDED
#define RECURSIVEGERENATOR_H_INCLUDED

#include "generator/Generator.h"
#include <stack>


class RecursiveGenerator : public Generator{
    public:
        RecursiveGenerator();
        virtual ~RecursiveGenerator();
        void generateMaze(class Maze&);
    private:
        /*!\ structure of generator grid type*/
        struct Cell{
            bool top_wall;
            bool bottom_wall;
            bool left_wall;
            bool right_wall;
            bool visited;
            int display_num;

            /*!\ default structure constructor
            */
            Cell()
            {
                top_wall = true;
                bottom_wall = true;
                left_wall = true;
                right_wall = true;
                visited = false;
                display_num =Maze::WALL;
            }
        };


        std::stack<COORD> back_track_coord;

        void setGridValue(class Maze&, const int&,const int &, const int&);

};

#endif // RECURSIVEGERENATOR_H_INCLUDED

#ifndef CONSOLECOLORCODE_H_INCLUDED
#define CONSOLECOLORCODE_H_INCLUDED

#define EMPTY 			-1
#define BLACK  			0
#define BLUE 			1
#define GREEN 			2
#define CYAN 			3
#define RED 			4
#define PURPLE 			5
#define YELLOW 			6
#define WHITE 			7
#define GRAY 			8
#define B_BLUE 			9
#define B_GREEN 		10
#define B_CYAN			11
#define B_RED			12
#define B_PURPLE		13
#define B_YELLOW		14
#define B_WHITE			15
#define BLACK_BLUE		16
#define BLUE_BLUE		17
#define GREEN_BLUE		18
#define CYAN_BLUE		19
#define RED_BLUE		20
#define PURPLE_BLUE		21
#define YELLOW_BLUE		22
#define WHITE_BLUE		23
#define GRAY_BLUE		24
#define B_BLUE_BLUE		25
#define B_GREEN_BLUE	26
#define B_CYAN_BLUE		27
#define B_RED_BLUE		28
#define B_PURPLE_BLUE	29
#define B_YELLOW_BLUE	30
#define B_WHITE_BLUE	31
#define BLACK_GREEN		32
#define BLUE_GREEN		33
#define GREEN_GREEN		34
#define CYAN_GREEN		35
#define RED_GREEN		36
#define PURPLE_GREEN	37
#define YELLOW_GREEN	38
#define WHITE_GREEN		39
#define GRAY_GREEN		40
#define B_BLUE_GREEN	41
#define B_GREEN_GREEN	42
#define B_CYAN_GREEN	43
#define B_RED_GREEN		44
#define B_PURPLE_GREEN	45
#define B_YELLOW_GREEN	46
#define B_WHITE_GREEN	47
#define BLACK_CYAN		48
#define BLUE_CYAN		49
#define GREEN_CYAN		50
#define CYAN_CYAN		51
#define RED_CYAN		52
#define PURPLE_CYAN		53
#define YELLOW_CYAN		54
#define WHITE_CYAN		55
#define GRAY_CYAN		56
#define B_BLUE_CYAN		57
#define B_GREEN_CYAN	58
#define B_CYAN_CYAN		59
#define B_RED_CYAN		60
#define B_PURPLE_CYAN	61
#define B_YELLOW_CYAN	62
#define B_WHITE_CYAN	63
#define BLACK_RED		64
#define BLUE_RED		65
#define GREEN_RED		66
#define CYAN_RED		67
#define RED_RED			68
#define PURPLE_RED		69
#define YELLOW_RED		70
#define WHITE_RED		71
#define GRAY_RED		72
#define B_BLUE_RED		73
#define B_GREEN_RED		74
#define B_CYAN_RED		75
#define B_RED_RED		76
#define B_PURPLE_RED	77
#define B_YELLOW_RED	78
#define B_WHITE_RED		79
#define BLACK_PURPLE	80
#define BLUE_PURPLE		81
#define GREEN_PURPLE	82
#define CYAN_PURPLE		83
#define RED_PURPLE		84
#define PURPLE_PURPLE	85
#define YELLOW_PURPLE	86
#define WHITE_PURPLE	87
#define GRAY_PURPLE		88
#define B_BLUE_PURPLE	89
#define B_GREEN_PURPLE	90
#define B_CYAN_PURPLE	91
#define B_RED_PURPLE	92
#define B_PURPLE_PURPLE	93
#define B_YELLOW_PURPLE	94
#define B_WHITE_PURPLE	95
#define BLACK_YELLOW	96
#define BLUE_YELLOW		97
#define GREEN_YELLOW	98
#define CYAN_YELLOW		99
#define RED_YELLOW		100
#define PURPLE_YELLOW	101
#define YELLOW_YELLOW	102
#define WHITE_YELLOW	103
#define GRAY_YELLOW		104
#define B_BLUE_YELLOW	105
#define B_GREEN_YELLOW	106
#define B_CYAN_YELLOW	107
#define B_RED_YELLOW	108
#define B_PURPLE_YELLOW	109
#define B_YELLOW_YELLOW	110
#define B_WHITE_YELLOW	111
#define BLACK_WHITE		112
#define BLUE_WHITE		113
#define GREEN_WHITE		114
#define CYAN_WHITE		115
#define RED_WHITE		116
#define PURPLE_WHITE	117
#define YELLOW_WHITE	118
#define WHITE_WHITE		119
#define GRAY_WHITE		120
#define B_BLUE_WHITE	121
#define B_GREEN_WHITE	122
#define B_CYAN_WHITE	123
#define B_RED_WHITE		124
#define B_PURPLE_WHITE	125
#define B_YELLOW_WHITE	126
#define B_WHITE_WHITE	127
#define BLACK_GRAY		128
#define BLUE_GRAY		129
#define GREEN_GRAY		130
#define CYAN_GRAY		131
#define RED_GRAY		132
#define PURPLE_GRAY		133
#define YELLOW_GRAY		134
#define WHITE_GRAY		135
#define GRAY_GRAY		136
#define B_BLUE_GRAY		137
#define B_GREEN_GRAY	138
#define B_CYAN_GRAY		139
#define B_RED_GRAY		140
#define B_PURPLE_GRAY	141
#define B_YELLOW_GRAY	142
#define B_WHITE_GRAY	143
#define  BLACK_B_BLUE	144
#define BLUE_B_BLUE		145
#define GREEN_B_BLUE	146
#define CYAN_B_BLUE		147
#define RED_B_BLUE		148
#define PURPLE_B_BLUE	149
#define YELLOW_B_BLUE	150
#define WHITE_B_BLUE	151
#define GRAY_B_BLUE		152
#define B_BLUE_B_BLUE	153
#define B_GREEN_B_BLUE	154
#define B_CYAN_B_BLUE	155
#define B_RED_B_BLUE	156
#define B_PURPLE_B_BLUE	157
#define B_YELLOW_B_BLUE	158
#define B_WHITE_B_BLUE	159
#define BLACK_B_GREEN	160
#define BLUE_B_GREEN	161
#define GREEN_B_GREEN	162
#define CYAN_B_GREEN	163
#define RED_B_GREEN		164
#define PURPLE_B_GREEN	165
#define YELLOW_B_GREEN	166
#define WHITE_B_GREEN	167
#define GRAY_B_GREEN	168
#define B_BLUE_B_GREEN	169
#define B_GREEN_B_GREEN	170
#define B_CYAN_B_GREEN	171
#define B_RED_B_GREEN	172
#define B_PURPLE_B_GREEN 173
#define B_YELLOW_B_GREEN 174
#define B_WHITE_B_GREEN	175
#define BLACK_B_CYAN	176
#define BLUE_B_CYAN		177
#define GREEN_B_CYAN	178
#define CYAN_B_CYAN		179
#define RED_B_CYAN		180
#define PURPLE_B_CYAN	181
#define YELLOW_B_CYAN	182
#define WHITE_B_CYAN	183
#define GRAY_B_CYAN		184
#define B_BLUE_B_CYAN	185
#define B_GREEN_B_CYAN	186
#define B_CYAN_B_CYAN	187
#define B_RED_B_CYAN	188
#define B_PURPLE_B_CYAN	189
#define B_YELLOW_B_CYAN	190
#define B_WHITE_B_CYAN	191
#define BLACK_B_RED		192
#define BLUE_B_RED		193
#define GREEN_B_RED		194
#define CYAN_B_RED		195
#define RED_B_RED		196
#define PURPLE_B_RED	197
#define YELLOW_B_RED	198
#define WHITE_B_RED		199
#define GRAY_B_RED		200
#define B_BLUE_B_RED	201
#define B_GREEN_B_RED	202
#define B_CYAN_B_RED	203
#define B_RED_B_RED		204
#define B_PURPLE_B_RED	205
#define B_YELLOW_B_RED	206
#define B_WHITE_B_RED	207
#define BLACK_B_PURPLE	208
#define BLUE_B_PURPLE	209
#define GREEN_B_PURPLE	210
#define CYAN_B_PURPLE	211
#define RED_B_PURPLE	212
#define PURPLE_B_PURPLE	213
#define YELLOW_B_PURPLE	214
#define WHITE_B_PURPLE	215
#define GRAY_B_PURPLE	216
#define B_BLUE_B_PURPLE	217
#define B_GREEN_B_PURPLE 218
#define B_CYAN_B_PURPLE	219
#define B_RED_B_PURPLE	220
#define B_PURPLE_B_PURPLE 221
#define B_YELLOW_B_PURPLE 222
#define B_WHITE_B_PURPLE 223
#define BLACK_B_YELLOW	224
#define BLUE_B_YELLOW	225
#define GREEN_B_YELLOW	226
#define CYAN_B_YELLOW	227
#define RED_B_YELLOW	228
#define PURPLE_B_YELLOW	229
#define YELLOW_B_YELLOW	230
#define WHITE_B_YELLOW	231
#define GRAY_B_YELLOW	232
#define B_BLUE_B_YELLOW	233
#define B_GREEN_B_YELLOW 234
#define B_CYAN_B_YELLOW	235
#define B_RED_B_YELLOW	236
#define B_PURPLE_B_YELLOW 237
#define B_YELLOW_B_YELLOW 238
#define B_WHITE_B_YELLOW 239
#define BLACK_B_WHITE	240
#define BLUE_B_WHITE	241
#define GREEN_B_WHITE	242
#define CYAN_B_WHITE	243
#define RED_B_WHITE		244
#define PURPLE_B_WHITE	245
#define YELLOW_B_WHITE	246
#define WHITE_B_WHITE	247
#define GRAY_B_WHITE	248
#define B_BLUE_B_WHITE	249
#define B_GREEN_B_WHITE	250
#define B_CYAN_B_WHITE	251
#define B_RED_B_WHITE	252
#define B_PURPLE_B_WHITE 253
#define B_YELLOW_B_WHITE 254
#define B_WHITE_B_WHITE 255

#endif // CONSOLECOLORCODE_H_INCLUDED

#ifndef CONSOLEFIX_H_INCLUDED
#define CONSOLEFIX_H_INCLUDED

#include <windows.h>
#include"gui/ConsoleColorCode.h"
#include<iostream>

class ConsoleFix{
    public:
        ConsoleFix();
        virtual ~ConsoleFix();
        void displayChar(const int&,const int&,const int &,const COORD& );
        void displayString(const std::string &,const bool&,const COORD&);
        void displayString(const char* ,const bool&,const COORD&);
        void resizeConsole(const int& width,const int& height);
        void gotoXY(const int& ,const int& );
    protected:

    private:
        const int bold_color;/*!< bold color of display string function */
        WORD color_word[27];
        WORD normal_color[27];
};

#endif // CONSOLEFIX_H_INCLUDED

#ifndef CONSOLESIMULATION_H_INCLUDED
#define CONSOLESIMULATION_H_INCLUDED

#include "gui/ConsoleFix.h"
#include "logic/Maze.h"
#include"logic/IRobot.h"
#include"logic/IRobotLog.h"
#include <deque>

class ConsoleSimulation
{
    public:
        ConsoleSimulation();
        virtual~ConsoleSimulation();
        void drawMaze(const class Maze&);
        void drawRobot(const class IRobot&);
        void drawBorder();
        void drawGuide();
        int handleEvent(const class Maze& , const class IRobot&,const int &);
        void addMonitor(const std::string&);
        void addConsole(const std::string&);
        void displayMonitor() const;
        void displayConsole() const;
    private:
        void  clearMonitor();
        void  clearConsole();
        void  newMaze(const class IRobot&, const class Maze&);
        void  reDrawTarget(const class Maze&);

        const int JUMP_STEP;
        const int BLOCK ;
        const int ARROW_RIGHT;
        const int ARROW_LEFT;
        const int ARROW_UP;
        const int ARROW_DOWN;
        const int ROBOT_STUN_TIME;

        const int MONITOR_HEIGHT;
        const int CONSOLE_HEIGHT;
        const int DISPLAY_WIDTH;
        const int BUTTON_DELAY;


        COORD board_start_point;
        COORD maze_start_point;
        COORD last_finish;
        class ConsoleFix *console_fix;

        int maze_width;
        int maze_height;
        int maze_size;
        int gen_num;
        int sleep_time_pos ;
        int monitor_index;
        int console_index;

        bool robot_start;
        bool change_target;

        std::deque<std::string> monitor_deque;
        std::deque<std::string> console_deque;

        std::string controller_name;

        void clearMaze();
};

#endif // CONSOLESIMULATION_H_INCLUDED

#ifndef IROBOT_H_INCLUDED
#define IROBOT_H_INCLUDED

#include "gui/ConsoleColorCode.h"
#include "logic/Maze.h"

#define NORMAL B_GREEN_GRAY
#define HIT_WALL B_GREEN_B_RED
#define FINISH B_GREEN_B_BLUE
#define MONITOR_WIDTH 25

class IRobot
{
public :
    static const int NORTH =1000;
    static const int EAST  =1001;
    static const int SOUTH =1002;
    static const int WEST  =1003;
    static const int AHEAD =2000;
    static const int RIGHT =2001;
    static const int BEHIND =2002;
    static const int LEFT =2003;
    static const int CENTRE=2004;
    static const int WALL =3000;
    static const int PASSAGE =3001;
    static const int BEENBEFORE =4000;
    IRobot();
    virtual ~IRobot();

    COORD        getLocation()      const;
    int          getLocationX()     const;
    int          getLocationY()     const;
    COORD        getPreLocation()   const;
    int          getPreLocationX()  const;
    int          getPreLocationY()  const;
    COORD        getTargetLocation()        const;
    int          getHeading()     const;
    bool         getActive()        const;
    int          getState()         const;
    int          getSteps()         const;
    int          getCollisions()    const;
    int          getRight()         const;
    int          getLeft()          const;
    int          getRunTime()       const;
    int          getBehind()        const;
    int          getAhead()         const;
    int          getPreDirection()  const;
    unsigned int getSleepTime()     const;
    std::string  getControllerName()const;
    bool         getInfoPermission()const;
    std::string  getConsoleInfo() ;


    void         setHeading(const int&);
    void         setMaze(const class Maze&);
    void         setControllerName(const std::string&);
    void         setState(const int& );
    void         setTarget(const COORD&);
    void         setTarget(const int&, const int&);
    void 		 setCollisionSquare(const int&,const int&,const bool&);
	void         clearLog();

    void         face(int) ;
    bool         facingWall() const;
    void         advance();
    int          look(int) const;
    int          handleEvent(const int&);
    void         defaultController();
    void         displayMoveReport();
    void         printLog(std::string);
    void         printLog(int);
    void         printLogEndl(std::string);
    void         printLogEndl(int);

private:
    COORD location;             /*!< Present location of the robot*/
    COORD pre_location;         /*!< previous location of the robot*/
    COORD target;               /*!< the target location */

    int state;                  /*!< hold the color of the robot through section*/

    bool active ;               /*!< the robot start or not*/
    bool **collision_track;     /*!< hold the info of the been before cell or new path*/
    bool getInfo;
    bool change_target;

    unsigned int steps;         /*!< the number of step robot has take*/
    unsigned int collisions;    /*!< the number of collision steps haw made*/
    unsigned int direction;     /*!< Robot geometry direction*/
    unsigned int pre_direction; /*!< Robot previous direction*/
    unsigned int sleep_time ;   /*!< robot sleep time*/
    unsigned int turn_right;    /*!< number of robot turn right*/
    unsigned int turn_left;     /*!< number of time robot turn left*/
    unsigned int run_time;      /*!< number of robot run time*/
    unsigned int turn_behind;   /*!< number of turn backward robot*/
    unsigned int go_ahead;      /*!< number of robot go ahead */


    std::string controller_name; /*!< hold the name of the student controller */
    std::string console_string; /*!< hold the print string of the user passing in */

    class Maze maze;            /*!< robot maze var*/

    bool          checkCollision(const COORD& )const;
    void          start();
    void          restart();

    void          setLocation(const COORD&);
    void          setLocation(const int&, const int&);
    void          setPreLocation(const COORD&);
    void          setPreLocation(const int&, const int&);
    void          setSleepTime(const unsigned int&);

    void          setSteps(const unsigned int &)         ;
    void          setCollisions(const unsigned int &)    ;
    void          setRight(const unsigned int &)         ;
    void          setLeft(const unsigned int &)          ;
    void          setRunTime(const unsigned int &)       ;
    void          setBehind(const unsigned int &)        ;
    void          setAhead(const unsigned int &)         ;
};

#endif // IROBOT_H_INCLUDED

#ifndef IROBOTLOG_H_INCLUDED
#define IROBOTLOG_H_INCLUDED

#include "logic/IRobot.h"
#define CONSOLE_WIDTH 25
class IRobotLog
{
    public :
        IRobotLog();
        virtual ~IRobotLog();
        void analysis(class IRobot&);
        void analysisLastRun(const class IRobot&) ;

        std::string getAnalysis() ;
        std::string getLastRunAnalysis() ;
    protected:
    private:
        std::string last_move;
        std::string last_run;
        std::string toString(const int& ) const ;

};

#endif // IROBOTLOG_H_INCLUDED

#ifndef LOGIC_H_INCLUDED
#define LOGIC_H_INCLUDED

#include "logic/Maze.h"
#include "logic/IRobot.h"
#include "logic/IRobotLog.h"
#include "generator/GeneratorSystem.h"


class Logic
{
    public :
        Logic();
        virtual ~Logic();
        int handleEvent(const int& );
        void controller(void (*control)(class IRobot&));
        void controller();

        Maze getMaze() const;
        IRobot getRobot() const;
        std::string getStepAnalysis() const;
        std::string getRunAnalysis() const;

    protected:
    private:
        const int SIZE_1;            /*!< 10x10 maze size*/
        const int SIZE_2;            /*!< 20x20 maze size*/
        const int SIZE_3;            /*!< 30x30 maze size*/
        bool change_target;
        unsigned int maze_size;      /*!< the default size of the maze */
        Maze* maze;
        IRobot* robot;
        IRobotLog* robot_log;
        GeneratorSystem *generator;
        bool manual;

};

#endif // LOGIC_H_INCLUDED

#ifndef MAZE_H_INCLUDED
#define MAZE_H_INCLUDED

#include<windows.h>
#include<fstream>
#include<iostream>
#include<malloc.h>

#include "eventlistener/KeyboardListener.h"

class Maze
{
    public :
        Maze();
        Maze(const int& ,const int&);
        Maze(std::string);
        virtual ~Maze();

        static const int MAX     =15;
        static const int WALL    =2;
        static const int PASSAGE =1;

        int getWidth() const;
        int getHeight() const;
        int getGridValue(const int& , const int& )const;
        int getGridValue(const COORD& )const;
        COORD getStart() const;
        COORD getFinish() const;
        int**getGrid() const;

        void setWidth(const int&);
        void setHeight(const int&);
        void setStart(const int & ,const int&);
        void setStart(const COORD &);
        void setFinish(const int & ,const int&);
        void setFinish(const COORD &);
        void setGridValue(const int& , const int&, const int&);
        void setGridValue(const COORD&, const int &);

        Maze& operator= (const class Maze&);


    protected:

    private:
        int** grid;         /*!< var hold the information of maze WALL or PASSAGE*/
        int width;          /*!< contain maze width*/
        int height;         /*!< contain maze height*/
        COORD start_point;  /*!< contain maze start point */
        COORD finish_point; /*!< contain maze finish point*/

        void saveToFile();
};

#endif // MAZE_H_INCLUDED

#ifndef MAZELOGIC_H_INCLUDED
#define MAZELOGIC_H_INCLUDED

#include "logic/Logic.h"
#include "gui/ConsoleSimulation.h"
#include "eventlistener/KeyboardListener.h"
#include <time.h>

class MazeLogic{
    public :
        MazeLogic();
        virtual ~MazeLogic();
        void start(void (*control)(class IRobot& ));
        void start();
    private:
        Logic *logic;
        bool program_exist;
        ConsoleSimulation *console_simulation;
};

#endif // MAZELOGIC_H_INCLUDED


#include "logic/MazeLogic.h"

void controller(IRobot& robot);

int main()
{
    MazeLogic maze_logic = MazeLogic();
    maze_logic.start(controller);

    return 0;
}

//** start of RobotController */
//** Sử dụng đoạn mã: bỏ chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Uncomment
//  * Sau khi sử dụng: chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Comment
//  */
//void controller(IRobot& robot)
//{
//    robot.advance(); // move the robot
//}
//** end of RobotController */



//** start of DumbController */
//** Sử dụng đoạn mã: bỏ chú thích đoạn mã
// * Bôi đen đoạn mã -> Chọn Edit -> Chọn Uncomment
//  * Sau khi sử dụng: chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Comment
//  */
//void controller(IRobot& robot)
//{
// int direction;
// int random_number = rand() % 4;
// switch (random_number) {
// case 1: direction = IRobot::LEFT; break;
// case 2: direction = IRobot::RIGHT; break;
// case 3: direction = IRobot::BEHIND; break;
// default: direction = IRobot::AHEAD;
// }
// robot.face(direction);
// robot.advance();
//}
//** end of DumbController */



//** start of DumbController switch */
//** Sử dụng đoạn mã: bỏ chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Uncomment
//  * Sau khi sử dụng: chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Comment
//  */
//void controller(IRobot& robot)
//{
//    int direction;
//
//    int random_number = rand() % 4;     // Select a random number 0, 1, 2, 3
//    switch (random_number)              // Convert this to a direction
//    {
//        case  1: direction = IRobot::LEFT;   break;
//        case  2: direction = IRobot::RIGHT;  break;
//        case  3: direction = IRobot::BEHIND; break;
//        default: direction = IRobot::AHEAD;  break;
//    }
//
//    robot.face(direction);              // Face the robot in this direction
//    robot.advance();                    // and move the robot
//
//
//}
//** end of DumbController switch */
//
//
//
//** start of BrokenController */
//** Sử dụng đoạn mã: bỏ chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Uncomment
//  * Sau khi sử dụng: chú thích đoạn mã
//  * Bôi đen đoạn mã -> Chọn Edit -> Chọn Comment
//  */

void controller(IRobot& robot)
{
    int direction = IRobot::AHEAD;
    int random_number;
    do
    {
        random_number = rand() % 4;      // Select a random number
        if (random_number == 0)             // Convert this to a direction
            direction = IRobot::LEFT;
        else if (random_number == 1)
            direction = IRobot::RIGHT;
        else if (random_number == 2)
            direction = IRobot::BEHIND;
        else
            direction = IRobot::AHEAD;
    } while (robot.look(direction) == IRobot::WALL || robot.look(direction) == IRobot::BEENBEFORE);

    robot.face(direction);          // Face the robot in this direction
    robot.advance();                // and move the robot

}
//** end of BrokenController */

