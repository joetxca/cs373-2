.DEFAULT_GOAL := all

JSFILES :=                  \
    Hello                   \
    UnitTests3              \
    Coverage1               \
    Coverage2               \
    Coverage3               \
    Exceptions              \
    StrCmpT                 \
    Types                   \
    Operators               \
    Reduce                  \
    ReduceT                 \
    Iteration               \
    RangeIterator           \
    RangeIteratorT          \
    Yield                   \
    Range                   \
    RangeT                  \
    Map                     \
    MapT                    \
    Functions               \
    FunctionDefaults        \
    FunctionUnpacking

PFILES :=                   \
    Hello                   \
    UnitTests3              \
    Coverage1               \
    Coverage2               \
    Coverage3               \
    IsPrime                 \
    IsPrimeT                \
    Exceptions              \
    StrCmpT                 \
    Types                   \
    Operators               \
    Factorial               \
    Reduce                  \
    ReduceT                 \
    Iteration               \
    RangeIterator           \
    RangeIteratorT          \
    Yield                   \
    Range                   \
    RangeT                  \
    Comprehensions          \
    Map                     \
    MapT                    \
    Iterables               \
    Functions               \
    FunctionKeywords        \
    FunctionDefaults        \
    FunctionUnpacking       \
    FunctionDict            \
    SelectT                 \
    ProjectT                \
    RegExps                 \
    CrossJoinT              \
    ThetaJoinT              \
    NaturalJoinT            \
    Decorators              \
    SingletonPattern

%.jsx: %.js
	-jshint $<
	istanbul cover _mocha -- $<

.pylintrc:
	pylint --disable=locally-disabled --reports=no --generate-rcfile > $@

%.pyx: %.py .pylintrc
	-mypy     $<
	-pylint   $<
	-coverage run    --branch $<
	-coverage report -m

all:

clean:
	rm -f  .coverage
	rm -f  .pylintrc
	rm -rf .mypy_cache

docker:
	docker run -it -v $(PWD):/usr/cs373 -w /usr/cs373 gpdowning/gcc

run: $(JSFILES:=.jsx) $(PFILES:=.pyx)

travis:
	make clean
	ls -al
	make run
	ls -al
