# TickTackGame
An old days game
package com.example.ticktackgame;

import androidx.appcompat.app.AppCompatActivity;

import android.graphics.Color;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.Switch;
import android.widget.Toast;

import java.sql.Array;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.Map;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void BuClick(View view) {
        Button buSelected = (Button) view;
        buSelected.setBackgroundColor(Color.RED);
        int CellID =0;
        switch ((buSelected.getId())){
            case R.id.bu1: CellID = 1;
            break;

            case R.id.bu2: CellID = 2;
                break;

            case R.id.bu3: CellID = 3;
                break;

            case R.id.bu4: CellID = 4;
                break;

            case R.id.bu5: CellID = 5;
                break;

            case R.id.bu6: CellID = 6;
                break;

            case R.id.bu7: CellID = 7;
                break;

            case R.id.bu8: CellID = 8;
                break;

            case R.id.bu9: CellID = 9;
                break;
        }
        Playgame(CellID, buSelected);
    }
    int ActivePlayer = 1;
    ArrayList<Integer> Player1 = new ArrayList<Integer>();
    ArrayList<Integer> Player2 = new ArrayList<Integer>();

    void Playgame (int CellID, Button buSelected){
       // Log.d( tag: "Player:", String.valueOf(CellID));
        if (ActivePlayer==1){
            buSelected.setText("X");
            buSelected.setBackgroundColor(Color.GREEN);
            Player1.add(CellID);
            ActivePlayer=2;

        }
        else if (ActivePlayer==2){
            buSelected.setText("O");
            buSelected.setBackgroundColor(Color.BLUE);
            Player2.add(CellID);
            ActivePlayer=1;

        }
        buSelected.setEnabled(false);
        Checkwinner();
    }
    void Checkwinner (){
        int Winner = -1;
        if (Player1.contains(1)&& Player1.contains(2)&& Player1.contains(3)) {
            Winner = 1;
        }
        if (Player2.contains(1)&& Player2.contains(2)&& Player2.contains(3)) {
            Winner = 2;
        }
        if (Player1.contains(4)&& Player1.contains(5)&& Player1.contains(6)) {
            Winner = 1;
        }
        if (Player2.contains(4)&& Player2.contains(5)&& Player2.contains(6)) {
            Winner = 2;
        }
        if (Player1.contains(7)&& Player1.contains(8)&& Player1.contains(9)) {
            Winner = 1;
        }
        if (Player2.contains(7)&& Player2.contains(8)&& Player2.contains(9)) {
            Winner = 2;
        }

        if (Player1.contains(1)&& Player1.contains(4)&& Player1.contains(7)) {
            Winner = 1;
        }
        if (Player2.contains(1)&& Player2.contains(4)&& Player2.contains(7)) {
            Winner = 2;
        }
        if (Player1.contains(2)&& Player1.contains(5)&& Player1.contains(8)) {
            Winner = 1;
        }
        if (Player2.contains(2)&& Player2.contains(5)&& Player2.contains(8)) {
            Winner = 2;
        }
        if (Player1.contains(3)&& Player1.contains(6)&& Player1.contains(9)) {
            Winner = 1;
        }
        if (Player2.contains(3)&& Player2.contains(6)&& Player2.contains(9)) {
            Winner = 2;
        }
        if (Winner!= -1) {
            if (Winner == 1) {
                Toast.makeText(this, "Player 1 is the Winner", Toast.LENGTH_LONG).show();
            }
            if (Winner == 2) {
                Toast.makeText(this, "Player 2 is the Winner", Toast.LENGTH_LONG).show();
            }
        }
        }
    }
