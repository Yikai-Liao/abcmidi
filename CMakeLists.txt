cmake_minimum_required(VERSION 3.20)
project(abcmidi)
set(CMAKE_C_STANDARD 90)

# define a series of variables to hold the source files
set(parseabc parseabc.c abc.h parseabc.h)
set(parser2 parser2.c abc.h parseabc.h parser2.h)
set(toabc toabc.c abc.h parseabc.h)
set(genmidi genmidi.c abc.h midifile.h genmidi.h)
set(store store.c abc.h parseabc.h midifile.h genmidi.h)
set(queues queues.c genmidi.h)
set(midifile midifile.c midifile.h)
set(midi2abc midi2abc.c midifile.h)
set(midicopy midicopy.c midicopy.h)
set(abcmatch abcmatch.c abc.h)
set(crack crack.c)
set(mftext mftext.c midifile.h)
set(yapstree yapstree.c abc.h parseabc.h structs.h drawtune.h)
set(drawtune drawtune.c structs.h sizes.h abc.h drawtune.h)
set(pslib pslib.c drawtune.h)
set(position position.c abc.h structs.h sizes.h)
set(debug debug.c structs.h abc.h)
set(matchsup matchsup.c abc.h parseabc.h parser2.h)

# add the executable
add_executable(abc2midi ${parseabc} ${store} ${genmidi} ${midifile} ${queues} ${parser2} stresspat.c)
add_executable(abc2abc ${parseabc} ${toabc})
add_executable(midi2abc ${midifile} ${midi2abc})
add_executable(mftext ${midifile} ${mftext} ${crack})
add_executable(yaps ${parseabc} ${yapstree} ${drawtune} ${debug} ${pslib} ${position} ${parser2})
add_executable(midicopy ${midicopy})
add_executable(abcmatch ${abcmatch} ${matchsup} ${parseabc})


