package coverage

import (
	"os"
	"testing"
	"time"
)

var ps People

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func TestMain(m *testing.M) {
	ps = People{
		{"1", "2", time.Now()},
		{"3", "4", time.Now().Add(time.Hour)},
		{"5", "6", time.Now().Add(time.Minute)},
	}
	m.Run()
}

func TestLen(t *testing.T) {
	if ps.Len() != 3 {
		t.Errorf("want %d, got %d", 1, ps.Len())
	}
}

func TestSwap(t *testing.T) {
	p0 := ps[0]
	p1 := ps[1]
	p2 := ps[2]
	ps.Swap(0, 2)
	if p0 != ps[2] || p1 != ps[1] || p2 != ps[0] {
		t.Errorf("Swap failed")
	}
	ps.Swap(0, 2)
}

func TestLess(t *testing.T) {
	if ps.Less(0, 1) {
		t.Errorf("want false, got true")
	}
	buf1 := ps[1].birthDay
	ps[1].birthDay = ps[0].birthDay
	if ps.Less(1, 0) {
		t.Errorf("want false, got true")
	}
	buf2 := ps[1].firstName
	ps[1].firstName = ps[0].firstName
	if ps.Less(1, 0) {
		t.Errorf("want false, got true")
	}
	ps[1].firstName = buf2
	ps[1].birthDay = buf1
}

func TestMatrix(t *testing.T) {
	res, err := New("test string")
	if err == nil || res != nil {
		t.Errorf("error missing")
	}
	res, err = New("1 2 3\n1 2")
	if err == nil || res != nil {
		t.Errorf("error %s", err)
	}
	res, err = New("1 2 3")
	if err != nil || res == nil {
		t.Errorf("error %s", err)
	}
	rows := res.Rows()
	if rows[0][0] != 1 || rows[0][1] != 2 || rows[0][2] != 3 || len(rows) != 1 {
		t.Errorf("wrong rows")
	}
	cols := res.Cols()
	if cols[0][0] != 1 || cols[1][0] != 2 || cols[2][0] != 3 || len(cols) != 3 {
		t.Errorf("wrong cols")
	}
	if !res.Set(0, 0, 4) {
		t.Errorf("want true, got false")
	}
	if res.Set(4, 0, 4) {
		t.Errorf("want false, got true")
	}
}
