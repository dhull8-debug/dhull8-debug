<xml xmlns="http://www.w3.org/1999/xhtml">
  <block type="trade_definition" id="trade_definition" x="20" y="20">
    <field name="MARKET">synthetic_index</field>
    <field name="SYMBOL">R_100</field>
    <field name="CONTRACT_TYPE">DIGITMATCH</field>
    <field name="DURATION">1</field>
    <field name="DURATION_UNIT">t</field>
    <field name="CURRENCY">USD</field>
    <field name="AMOUNT">1</field>
    <field name="BASIS">stake</field>
    <field name="PREDICTION">5</field>
  </block>
  <block type="trade_once" id="start_trade">
    <next>
      <block type="controls_if" id="trade_outcome">
        <value name="IF0">
          <block type="check_result" id="check_win">
            <field name="CHECK_RESULT">win</field>
          </block>
        </value>
        <statement name="DO0">
          <block type="variables_set" id="reset_stake">
            <field name="VAR">stake</field>
            <value name="VALUE">
              <block type="math_number" id="initial_stake">
                <field name="NUM">1</field>
              </block>
            </value>
          </block>
        </statement>
        <next>
          <block type="controls_if" id="check_lose">
            <value name="IF0">
              <block type="check_result" id="check_loss">
                <field name="CHECK_RESULT">loss</field>
              </block>
            </value>
            <statement name="DO0">
              <block type="variables_set" id="double_stake">
                <field name="VAR">stake</field>
                <value name="VALUE">
                  <block type="math_arithmetic" id="double_stake_calc">
                    <field name="OP">MULTIPLY</field>
                    <value name="A">
                      <block type="variables_get" id="current_stake">
                        <field name="VAR">stake</field>
                      </block>
                    </value>
                    <value name="B">
                      <block type="math_number" id="multiplier">
                        <field name="NUM">2</field>
                      </block>
                    </value>
                  </block>
                </value>
              </block>
              <next>
                <block type="controls_if" id="max_loss_streak">
                  <value name="IF0">
                    <block type="logic_compare" id="compare_losses">
                      <field name="OP">EQ</field>
                      <value name="A">
                        <block type="variables_get" id="loss_count">
                          <field name="VAR">losses</field>
                        </block>
                      </value>
                      <value name="B">
                        <block type="math_number" id="max_streak_limit">
                          <field name="NUM">10</field>
                        </block>
                      </value>
                    </block>
                  </value>
                  <statement name="DO0">
                    <block type="trade_action" id="stop_bot">
                      <field name="TRADE_ACTION">stop</field>
                    </block>
                  </statement>
                </block>
              </next>
            </statement>
          </block>
        </next>
      </block>
    </next>
  </block>
  <block type="variables_set" id="initialize_variables" inline="true" x="20" y="200">
    <field name="VAR">stake</field>
    <value name="VALUE">
      <block type="math_number" id="initial_stake_value">
        <field name="NUM">1</field>
      </block>
    </value>
  </block>
  <block type="trade_definition_restart" id="restart_trade" x="20" y="400">
    <field name="MARKET">synthetic_index</field>
    <field name="SYMBOL">R_100</field>
    <field name="CONTRACT_TYPE">DIGITMATCH</field>
    <field name="DURATION">1</field>
    <field name="DURATION_UNIT">t</field>
    <field name="CURRENCY">USD</field>
    <field name="AMOUNT">stake</field>
    <field name="BASIS">stake</field>
    <field name="PREDICTION">5</field>
  </block>
</xml>

