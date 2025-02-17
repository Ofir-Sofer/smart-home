CXX = g++
CC = $(CXX)

INCLUDES_DIR = ../../inc
SOURCES_DIR = ../../src

CFLAGS = -Wall -Werror -Wextra -pedantic -g -fPIC
CXXFLAGS = $(CFLAGS)
CXXFLAGS += -std=c++17 -I$(INCLUDES_DIR)

TARGET_TEMPATURE_SENSOR = libagent_tempature.so
OBJS_TEMPATURE_SENSOR = $(SOURCES_DIR)/agent_tempature.o $(SOURCES_DIR)/protocol.o $(SOURCES_DIR)/event.o\
						$(SOURCES_DIR)/agent_sensor.o

TARGET_ACCESS_SENSOR = libagent_access.so
OBJS_ACCESS_SENSOR = $(SOURCES_DIR)/agent_access.o $(SOURCES_DIR)/protocol.o $(SOURCES_DIR)/event.o\
						$(SOURCES_DIR)/agent_sensor.o

TARGET_AC_CONTROLER = libagent_ac.so
OBJS_AC_CONTROLER = $(SOURCES_DIR)/agent_ac.o $(SOURCES_DIR)/protocol.o $(SOURCES_DIR)/event.o

TARGET_DOOR_CONTROLER = libagent_door.so
OBJS_DOOR_CONTROLER = $(SOURCES_DIR)/agent_door.o $(SOURCES_DIR)/protocol.o $(SOURCES_DIR)/event.o

TARGET_WINDOW_CONTROLER = libagent_window.so
OBJS_WINDOW_CONTROLER = $(SOURCES_DIR)/agent_window.o $(SOURCES_DIR)/protocol.o $(SOURCES_DIR)/event.o

tempature_agent: $(TARGET_TEMPATURE_SENSOR)

access_agent: $(TARGET_ACCESS_SENSOR)

ac_agent: $(TARGET_AC_CONTROLER)

door_agent: $(TARGET_DOOR_CONTROLER)

window_agent: $(TARGET_WINDOW_CONTROLER)

$(TARGET_TEMPATURE_SENSOR): $(OBJS_TEMPATURE_SENSOR) 
	$(CC) $(CXXFLAGS) -shared -o $(TARGET_TEMPATURE_SENSOR) $(OBJS_TEMPATURE_SENSOR)

$(TARGET_ACCESS_SENSOR): $(OBJS_ACCESS_SENSOR) 
	$(CC) $(CXXFLAGS) -shared -o $(TARGET_ACCESS_SENSOR) $(OBJS_ACCESS_SENSOR)

$(TARGET_AC_CONTROLER): $(OBJS_AC_CONTROLER) 
	$(CC) $(CXXFLAGS) -shared -o $(TARGET_AC_CONTROLER) $(OBJS_AC_CONTROLER)

$(TARGET_DOOR_CONTROLER): $(OBJS_DOOR_CONTROLER) 
	$(CC) $(CXXFLAGS) -shared -o $(TARGET_DOOR_CONTROLER) $(OBJS_DOOR_CONTROLER)

$(TARGET_WINDOW_CONTROLER): $(OBJS_WINDOW_CONTROLER) 
	$(CC) $(CXXFLAGS) -shared -o $(TARGET_WINDOW_CONTROLER) $(OBJS_WINDOW_CONTROLER)

.c.o:
	$(CC) $(CXXFLAGS) -cpp $< -o $@

clean:
	$(RM) $(OBJS_TEMPATURE_SENSOR) $(TARGET_TEMPATURE_SENSOR)
	$(RM) $(OBJS_ACCESS_SENSOR) $(TARGET_ACCESS_SENSOR) 
	$(RM) $(OBJS_AC_CONTROLER) $(TARGET_AC_CONTROLER)
	$(RM) $(OBJS_DOOR_CONTROLER) $(TARGET_DOOR_CONTROLER)
	$(RM) $(OBJS_WINDOW_CONTROLER) $(TARGET_WINDOW_CONTROLER)

.PHONY: clean

$(SOURCES_DIR)/agent_tempature.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent_sensor.hpp
$(SOURCES_DIR)/agent_access.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent_sensor.hpp
$(SOURCES_DIR)/agent_ac.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent_controler.hpp
$(SOURCES_DIR)/agent_door.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent_controler.hpp
$(SOURCES_DIR)/agent_window.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent_controler.hpp
$(SOURCES_DIR)/protocol.o: $(INCLUDES_DIR)/protocol.hpp
$(SOURCES_DIR)/event.o: $(INCLUDES_DIR)/event.hpp
$(SOURCES_DIR)/agent_sensor.o: $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/event.hpp $(INCLUDES_DIR)/agent.hpp
$(INCLUDES_DIR)/agent_controler.hpp : $(INCLUDES_DIR)/protocol.hpp $(INCLUDES_DIR)/agent.hpp
