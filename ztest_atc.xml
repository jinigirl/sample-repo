*&---------------------------------------------------------------------*
*& Report  ZTEST_ATC
*&
*&---------------------------------------------------------------------*
*&
*&
*&---------------------------------------------------------------------*
Report  ZTEST_ATC.

CLASS zcl_math DEFINITION.

  PUBLIC SECTION.

  METHODS: get_sum IMPORTING num1 TYPE i
                             num2 TYPE i
                   EXPORTING sum1 TYPE i
                   RAISING cx_sy_arithmetic_error,

           get_diff IMPORTING num1 TYPE i
                              num2 TYPE i
                    EXPORTING diff TYPE i
                    RAISING cx_sy_arithmetic_error,

           get_prod IMPORTING num1 TYPE i
                              num2 TYPE i
                    EXPORTING prod TYPE i
                    RAISING cx_sy_arithmetic_error,

           get_quo  IMPORTING num1 TYPE i
                              num2 TYPE i
                    EXPORTING quo TYPE i
                    RAISING cx_sy_arithmetic_error.

ENDCLASS.

*&---------------------------------------------------------------------*
*&       Class (Implementation)  zcl_math
*&---------------------------------------------------------------------*
*        Text
*----------------------------------------------------------------------*
CLASS zcl_math IMPLEMENTATION.

  METHOD get_sum.
     sum1 = num1 * num2.

  ENDMETHOD.

    METHOD get_diff.
     diff = num1 - num2.

  ENDMETHOD.

    METHOD get_prod.
     prod = num1 * num2.

  ENDMETHOD.

    METHOD get_quo.
     quo = num1 / num2.

  ENDMETHOD.



ENDCLASS.               "zcl_math


CLASS lcl_test DEFINITION FOR TESTING.
  "#AU Risk_Level Harmless
  "#AU Duration   Short


  PUBLIC SECTION.

  DATA: o_math TYPE REF TO zcl_math,
        res TYPE i.

  METHODS: m_sum FOR TESTING,
           m_diff FOR TESTING,
           m_prod FOR TESTING,
           m_quo FOR TESTING.

ENDCLASS.               "lcl_test

*&---------------------------------------------------------------------*
*&       Class (Implementation)  lcl_test
*&---------------------------------------------------------------------*
*        Text
*----------------------------------------------------------------------*
CLASS lcl_test IMPLEMENTATION.

  METHOD: m_sum.

   CREATE OBJECT o_math.

   CALL METHOD o_math->get_sum( EXPORTING num1 = 4
                                          num2 = 2
                                IMPORTING sum1 = res ).

     cl_aunit_assert=>assert_equals(
       exp = 6
       act = res
       msg = 'Incorrect Sum!' ).

  ENDMETHOD.

 METHOD: m_diff.

   CREATE OBJECT o_math.

   CALL METHOD o_math->get_diff( EXPORTING num1 = 4
                                          num2 = 2
                                IMPORTING diff = res ).

     cl_aunit_assert=>assert_equals(
       exp = 2
       act = res
       msg = 'Incorrect Difference!' ).

  ENDMETHOD.

 METHOD: m_prod.

   CREATE OBJECT o_math.

   CALL METHOD o_math->get_prod( EXPORTING num1 = 4
                                          num2 = 2
                                IMPORTING prod = res ).

     cl_aunit_assert=>assert_equals(
       exp = 8
       act = res
       msg = 'Incorrect Product!' ).

  ENDMETHOD.

 METHOD: m_quo.

   CREATE OBJECT o_math.

   CALL METHOD o_math->get_quo( EXPORTING num1 = 4
                                          num2 = 2
                                IMPORTING quo = res ).

     cl_aunit_assert=>assert_equals(
       exp = 2
       act = res
       msg = 'Incorrect Quotient!' ).

  ENDMETHOD.


ENDCLASS.


START-OF-SELECTION.

 PARAMETERS: p_num1 TYPE i DEFAULT '4',
             p_num2 TYPE i DEFAULT '2'.

DATA: lo_math TYPE REF TO zcl_math,
      lv_sum TYPE i,
      lv_diff TYPE i,
      lv_prod TYPE i,
      lv_quo TYPE i.

CREATE OBJECT lo_math.


CALL METHOD lo_math->get_sum( EXPORTING num1 = p_num1
                                        num2 = p_num2
                              IMPORTING sum1 = lv_sum ).
CALL METHOD lo_math->get_diff( EXPORTING num1 = p_num1
                                        num2 = p_num2
                               IMPORTING diff = lv_diff ).
CALL METHOD lo_math->get_prod( EXPORTING num1 = p_num1
                                        num2 = p_num2
                               IMPORTING prod = lv_prod ).
CALL METHOD lo_math->get_quo( EXPORTING num1 = p_num1
                                        num2 = p_num2
                              IMPORTING quo = lv_quo ).

WRITE: / 'Sum: ', lv_sum,
       / 'Difference: ', lv_diff,
       / 'Product: ', lv_prod,
       / 'Quotient: ', lv_quo.
